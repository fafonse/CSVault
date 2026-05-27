Data Organization:

Merchant Table:
Partition Key: Name (str)
Sort Key: Token2 (double)

| Label        | Data Type    |     |
| ------------ | ------------ | --- |
| Token        | str          |     |
| Name         | str          |     |
| Bank Account | str (hashed) |     |


Bank Table:
Partition Key: Bank ID (int)
Sort Key: Account Balance (double)
Contains:

| Label   | Data Type |
| ------- | --------- |
| API Key | string    |
| Name    | string    |

 


Log Table:
Partition key: hashed_card_number#month (bucket transactions by month for hot spots)
Sort key: timestamp
Contains: 

| Label                | Data Type |     |
| -------------------- | --------- | --- |
| Card Number (hashed) | string    |     |
| Transaction Amount   | int       |     |
| Merchant ID          | int       |     |
| Bank ID              | int       |     |
| Merchant?            | bool      |     |
