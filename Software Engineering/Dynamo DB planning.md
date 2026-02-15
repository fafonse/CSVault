Data Organiztion:

Merchant Table:
Partition Key: Merchant ID
Sort Key: Account Balance

Bank Table:
Partition Key: Bank ID
Sort Key: Account Balance
Contains:

| Label   | Data Type |
| ------- | --------- |
| API Key | string    |
|         |           |

 


Log Table:
Partition key: hashed_card_number#month (bucket transactions by month for hot spots)
Sort key: timestamp
Contains: 

| Label              | Data Type |
| ------------------ | --------- |
| Card Number        | string    |
| Transaction Amount | int       |
| Merchant ID        | int       |
| Bank ID            | int       |
