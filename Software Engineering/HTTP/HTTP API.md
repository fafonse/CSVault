When building an API you have a couple requirements to follow. 

## Format
Header, body, and the status codes.
Your header contains the data type being requested/accepted.
The body has all of the meat of the data, structured in JSON.
Status codes are what your program returns, and they have specific meanings given to them.

## Design
When you're making your API, you should have a gateway layer (abstraction layer). The gateway is a middleman between your API functions and the users. 
Gateways have a couple advantages:
- Decouples functions from API access logic
- Increases API security
- Allows for more control/data from the access point

## Example

```python
import json

def lambda_handler(event, context):
	body = json.loads(event.get("body", "{}"))
	name = body.get("name")
	cc_num = body.get("card_num")
	amount = body.get("amount")
	
	return {
		"statusCode": 200,
		"headers" : {
			"Content-Type": "text/plain"
		},
		"body": f"name: {name}\ncard: {cc_num}\namount: {amount}}}"
```