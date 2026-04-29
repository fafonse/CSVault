## Code

### Lambda Function
```python
import datetime
import json
import socket
import urllib.error
import urllib.request
from decimal import Decimal
from time import sleep
from typing import NamedTuple

import boto3

import banks

FUNDS_ERROR = "Declined - Insufficient Funds."
INVALID_ERROR = "Declined - Invalid Bank or Card Information."
MERCHANT_ERROR = "Declined - Invalid Merchant Credentials."
BANK_ERROR = "Error - Bank Not Supported."
AVAILABLE_ERROR = "Error - Bank Not Available."
ACCEPTED_CODE = "Accepted."


class incomingRequest(NamedTuple):
    merchant_name: str
    merchant_token: str
    bank: str
    card_holder: str
    card_number: str
    card_type: str
    cvv: str
    card_zip: str
    exp_date: str
    amount: float
    timestamp: str


def lambda_handler(event, context):
    dynamodb = boto3.resource("dynamodb")  # ask ai about this
    table = dynamodb.Table("Merchants")
    bank_list = banks.getBankList()

    try:
        body = json.loads(event.get("body", "{}"))
        apiRequest = incomingRequest(
            body.get("merchant_name"),
            body.get("merchant_token"),
            body.get("bank").lower(),  # sanitize inputs a bit
            body.get("card_holder"),
            body.get("cc_number"),
            body.get("card_type").lower(),  # make it easy for us
            body.get("cvv"),
            body.get("card_zip"),
            body.get("exp_date"),
            float(body.get("amount")),
            body.get("timestamp"),
        )
    except (json.JSONDecodeError, TypeError):  # Check for decoding errors
        print("JSON decode error")
        return format_response(500, INVALID_ERROR)

    missing_fields = [
        field for field, value in apiRequest._asdict().items() if value is None
    ]
    if missing_fields:
        print("Missing fields:", missing_fields)  # check that all fields are filled
        return format_response(500, INVALID_ERROR)

    # merchant authentication
    if not authMerchant(table, apiRequest.merchant_name, apiRequest.merchant_token):
        return format_response(401, MERCHANT_ERROR)

    bank_name = apiRequest.bank
    if "joseph" in bank_name or "jank" in bank_name:  # lazy/manual input fixing
        bank_name = "joseph"
    elif "topher" in bank_name:
        bank_name = "topher"
    elif "west" in bank_name:
        bank_name = "west"
    elif "corbin" in bank_name:
        bank_name = "corbin"

    # check that bank is valid
    if bank_name not in bank_list:
        return format_response(400, BANK_ERROR)

    packer = bank_list[bank_name]["packer"]
    parser = bank_list[bank_name]["parser"]

    packed_data, url = packer(apiRequest)  # payload is tuple ... (body, header)
    payload = packed_data[0]
    header = packed_data[1]

    if url is None:
        return format_response(500, INVALID_ERROR)

    message, code = send_data(payload, header, url)

    print(payload)  # print after data is sent
    print(message)
    print(code)

    if code == 200:
        status = "Accepted"
    else:
        status = "Declined"

    if code == 504:
        return format_response(code, AVAILABLE_ERROR)

    message = json.loads(message)  # force json
    error, code = parser(code, message)

    log_data(
        apiRequest.merchant_name,
        apiRequest.bank,
        apiRequest.card_number,
        apiRequest.amount,
        status,
        code,
    )
    return format_response(code, error)


def authMerchant(table, name, token):  # check if merchant is in DB
    if not name or not token or not table:
        print("Authentication Error (merchant) - Bad Info")
        return False

    try:
        result = table.get_item(Key={"Name": name, "Token": token})
        return "Item" in result  # return if item is in there
    except Exception as e:
        print("DynamoDB get_item error:", repr(e))  # needs to go inside cloudwatch
        return False


def format_response(status, message):
    return {
        "statusCode": status,
        "headers": {"Content-Type": "application/json"},
        "body": json.dumps({"message": message}),
    }


def send_data(body, header, url):
    print("Sending data...")
    payload = json.dumps(body).encode("utf-8")

    wait_times = [0, 2, 4, 8]  # include first attempt (no wait)
    timeout = 2

    for attempt in range(len(wait_times)):
        wait = wait_times[attempt]

        if wait > 0:
            print(f"Retrying in {wait} seconds...")
            sleep(wait)

        try:
            print(f"Attempt {attempt + 1}: Sending payload to bank...")

            req = urllib.request.Request(
                url,
                data=payload,
                headers=header,
                method="POST",
            )

            with urllib.request.urlopen(req, timeout=timeout) as response:
                result = response.read().decode()
                print("Response received")
                return result, response.getcode()

        except urllib.error.HTTPError as e:
            print("HTTP Error:", e.code)
            error_body = e.read().decode()
            print(error_body)
            return error_body, e.code

        except (urllib.error.URLError, socket.timeout, TimeoutError) as e:
            print(f"Timeout on attempt {attempt + 1}: {e}")

            if attempt == len(wait_times) - 1:
                print("No more attempts remaining...")
                return "timeout", 504

        except Exception as e:
            print("Unexpected error:", e)
            return "error", 500

    print("Timed out fully, bank unresponsive")
    return "timeout", 504


def log_data(merchant, bank, cc_num, amount, status, code):
    dynamodb = boto3.resource("dynamodb")
    log_table = dynamodb.Table("Transactions")
    cc_num = str(cc_num)[-4:].zfill(4)

    log_entry = {
        "Bank#cc_number": bank + "#" + cc_num,
        "merchant": merchant,
        "bank": bank,
        "cc_number": cc_num,
        "amount": Decimal(str(amount)).quantize(
            Decimal("0.01")
        ),  # ensure no type errors
        "timestamp": str(
            datetime.datetime.utcnow().isoformat() + "Z"
        ),  # use my timestamp format to keep table sorting easy
        "status": status,
        "code": str(code),
    }

    log_table.put_item(Item=log_entry)
```

### Banks.py
```python
import os


# Standard Error Codes
FUNDS_ERROR = "Declined - Insufficient Funds."
INVALID_ERROR = "Declined - Invalid Bank or Card Information."
MERCHANT_ERROR = "Declined - Invalid Merchant Credentials."
BANK_ERROR = "Error - Bank Not Supported."
AVAILABLE_ERROR = "Error - Bank Not Available."
ACCEPTED_CODE = "Accepted."


def JeffBankPacker(request):
    cch_name = os.environ.get("jeff_name")
    cch_token = os.environ.get("jeff_token")
    url = os.environ.get("jeff_url")

    header = {"Content-Type": "application/json"}
    try:
        payload = {
            "cch_name": cch_name,
            "cch_token": cch_token,
            "card_holder": request.card_holder,
            "card_num": request.card_number,
            "exp_date": request.exp_date,
            "cvv": request.cvv,
            "card_zip": request.card_zip,
            "txn_type": request.card_type,
            "merchant": request.merchant_name,
            "amount": request.amount,
            "timestamp": request.timestamp,
        }
    except:
        return 0, None
    return (payload, header), url


def JeffBankParser(code, message):
    code_map = {
        200: ACCEPTED_CODE,
        400: INVALID_ERROR,
        401: AVAILABLE_ERROR,
        403: INVALID_ERROR,
        404: INVALID_ERROR,
    }
    error = code_map.get(code, AVAILABLE_ERROR)
    message = message.get("message")

    if "Missing" in message:
        code = 400
        error = INVALID_ERROR
    elif "Invalid" in message:
        code = 403
        error = INVALID_ERROR
    elif "Insufficient" in message:
        code = 200
        error = FUNDS_ERROR
    elif code == 403:  # accepted, but bad info
        code = 200

    return error, code


def CaliBearPacker(request):
    url = os.environ.get("calibear_url")  # must have trailing slash
    id = os.environ.get("calibear_id")
    key = os.environ.get("calibear_key")
    transaction_type = "withdrawal"  # we didn't do the merchant part lol
    card_number = request.card_number.zfill(16)  # ensure its 16 long

    header = {"Content-Type": "application/json", "x-api-key": key}
    payload = {
        "clearinghouse_id": id,
        "card_number": card_number,
        "amount": abs(float(request.amount)),  # must be a positive number
        "transaction_type": transaction_type,
        "merchant_name": request.merchant_name,
    }

    return (payload, header), url


def CaliBearParser(code, message):
    code_map = {
        200: ACCEPTED_CODE,
        400: INVALID_ERROR,
        401: AVAILABLE_ERROR,
        404: INVALID_ERROR,
        500: AVAILABLE_ERROR,
    }
    error = code_map.get(code, AVAILABLE_ERROR)

    if code == 400:
        print("Missing parameters for CaliBear Bank")
        print(message.get("message"))
    elif code == 404:
        error = 403
        error = INVALID_ERROR
    elif code == 403:
        if ("INSUFFICIENT", "CREDIT_LIMIT", "OVERDRAWN") in message.get("message"):
            code = 200
            error = FUNDS_ERROR
        if ("DAILY_LIMIT", "CLOSED") in message.get("message"):
            code = 200
            error = AVAILABLE_ERROR  # i don really know here, would need a diff error for this

    return error, code


def CorbinPacker(request):
    url = os.environ.get("corbin_url")
    username = os.environ.get("corbin_username")
    password = os.environ.get("corbin_password")
    card_number = request.card_number.zfill(16)
    header = {
        "Content-Type": "application/json",
        "username": username,
        "password": password,
    }
    payload = {
        "account_num": card_number,
        "cvv": request.cvv,
        "exp_date": request.exp_date,
        "amount": str(request.amount),
        "transaction_type": "withdrawal",  # easy lol
        "card_type": request.card_type.lower(),  # must be lowercase
    }
    return (payload, header), url


def CorbinParser(code, message):
    code_map = {
        200: ACCEPTED_CODE,
        400: INVALID_ERROR,
        401: BANK_ERROR,  # for bad credentials
        402: FUNDS_ERROR,
        404: INVALID_ERROR,
        502: INVALID_ERROR,
    }

    if code == 400:
        print("Missing parameters for Corbin Bank")
        print(message.get("message"))

    error = code_map.get(code, AVAILABLE_ERROR)
    return error, code


def TopherPacker(request):
    url = os.environ.get("topher_url")
    cch_name = os.environ.get("topher_name")
    cch_token = os.environ.get("topher_token")

    if request.card_type.lower() == "debit":
        withdrawal = True
    else:
        withdrawal = True

    header = {"Content-Type": "application/json"}
    payload = {
        "cch_name": cch_name,
        "cch_token": cch_token,
        "card_number": request.card_number,
        "cvv": request.cvv,
        "exp_date": request.exp_date,
        "amount": abs(request.amount),  # must be a positive number
        "transaction_type": request.card_type,
        "merchant_name": request.merchant_name,
        "withdrawal": withdrawal,
    }

    return (payload, header), url


def TopherParser(code, message):
    statusCode = message.get("statusCode")

    code_map = {
        200: ACCEPTED_CODE,  # could be declined
        400: BANK_ERROR,
        401: BANK_ERROR,
        404: INVALID_ERROR,  # could also be low $$
        500: AVAILABLE_ERROR,
    }
    error = code_map.get(statusCode, AVAILABLE_ERROR)

    return error, statusCode


def JosephPacker(request):
    url = os.environ.get("joseph_url")
    cch_name = os.environ.get("joseph_name")
    cch_token = os.environ.get("joseph_token")
    account_num = "ACCT1000" + request.card_number[-2:]

    header = {"Content-Type": "application/json"}
    payload = {
        "cch_name": cch_name,
        "cch_token": cch_token,
        "account_num": account_num,
        "card_num": request.card_number,
        "exp_date": request.exp_date,
        "cvv": request.cvv,
        "amount": str(request.amount),
        "type": request.card_type,
    }
    return (payload, header), url


def JosephParser(code, message):
    code_map = {
        200: ACCEPTED_CODE,
        400: INVALID_ERROR,
        401: INVALID_ERROR,
        403: FUNDS_ERROR,
        500: AVAILABLE_ERROR
    }

    error = code_map.get(code, AVAILABLE_ERROR)
    return error, code


def WestPacker(request):
    url = os.environ.get("west_url")
    cch_name = os.environ.get("west_name")
    cch_token = os.environ.get("west_token")
    transaction_type = "withdrawal"

    header = {"Content-Type": "application/json"}
    payload = {
        "cch_name": cch_name,
        "cch_token": cch_token,
        "account_holder_name": request.card_holder,
        "account_number": request.card_number,
        "transaction_type": transaction_type,
        "card_type": request.card_type,
        "amount": abs(request.amount),
    }
    return (payload, header), url


def WestParser(code, message):
    code_map = {
        200: ACCEPTED_CODE,
        401: INVALID_ERROR,
        400: INVALID_ERROR,
        500: AVAILABLE_ERROR,
    }
    if code != 200:
        print(message)
    error = code_map.get(code, AVAILABLE_ERROR)
    return error, code


# return tuple (payload, header)
# all banks are lowercase
banks = {
    "jeffs bank": {"packer": JeffBankPacker, "parser": JeffBankParser},
    "calibear": {"packer": CaliBearPacker, "parser": CaliBearParser},
    "corbin": {"packer": CorbinPacker, "parser": CorbinParser},
    "topher": {"packer": TopherPacker, "parser": TopherParser},
    "joseph": {"packer": JosephPacker, "parser": JosephParser},
    "west": {"packer": WestPacker, "parser": WestParser},
}


def getBankList():
    return banks
```
## Diagrams

### Component Diagram
![[final component.png]]
### Sequence Diagram
![[final sequence.png]]
### Flow Chart
![[Pasted image 20260428003923.png]]
### System Context Diagram
![[Pasted image 20260428004018.png]]
## User Stories
- *79* story points total
- *58* completed

**Remaining User stories:**
-  As a CEO I want a function to report on the API's current status
	- 5pts
- As a Developer I want Github Actions to test the code for deployment
	- 8pts
- As a Bank I want to Download my Logs
	- 8pts
	- We can just send them specific parts of the transaction log
		- So not a big deal

### Completed User Stories

| Points | Description                                                     |
| ------ | --------------------------------------------------------------- |
| 13     | As a POS I require that the Clearing House Works with all Banks |
| 8      | As a Developer I need a Testing Program for the API             |
| 5      | As a Developer I require a modular Bank data parser             |
| 5      | As a Maintainer I want to be able to Access Logs from AWS       |
| 5      | As a Bank I need Transaction Logs 5                             |
| 3      | As a Bank I want Clear, Readable Logs                           |
| 3      | As a Company I want my API parameters to be Secret              |
| 3      | As Bank I require Identifying Information for the Card          |
| 3      | As a Developer I want a Modular System                          |
| 2      | As a Maintainer I want to Monitor my API                        |
| 1      | As a POS I want Multiple Error Codes                            |
## Burn Down Chart

One thing to keep in mind is that I significantly struggled with the *timeout* assignment. This was due to the Jeffs Bank API timing out far too often, leading to my lambda function to timeout as well. The grading program that was given to the class was not built to handle a timing out bank API, leading to misleading and cryptic errors.

This explains the big fat camel hump for the most part.
![[Pasted image 20260428004855.png]]

## Transaction Reports
Due to time constraints, I wasn't able to create a visual report of my data. However, I was able to show the current state of the API with a text output.

> Corbin's bank pulls a 404 error no matter what. And the Wild West Bank does not have credentials.

```
Total transactions: 300
Failed transactions: 132
Failure ratio: 44.00%

Top error codes:
404: 64
401: 61
403: 5
400: 1
500: 1

Bank failure rates:
corbins bank: 64/64 (100.00%)
wild west bank: 61/61 (100.00%)
josephs bank: 5/57 (8.77%)
calibear: 2/46 (4.35%)
tophers bank: 0/63 (0.00%)
jeffs bank: 0/9 (0.00%)

Most error-prone bank: corbins bank (100.00% failure rate)
```