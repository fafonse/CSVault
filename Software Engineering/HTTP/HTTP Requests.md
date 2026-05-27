When using HTTP for API shit and non-website shit, you gotta understand how it works.

## Format
HTTP requests are usually done in JSON format. This means that it's pretty simple and universal for making requests.
## Python Usage
Python usage is really easy and simple. It includes the 
```python
import requests

url = "blahblahblah"

my_body = {'name' : 'Jeff',
		'card_num' : '197119638008',
		'amount' : '112.50'}

x = requests.post(url, json=myobj)

print(x.text)
```