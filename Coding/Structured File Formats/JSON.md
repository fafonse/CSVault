A key-value pair sort of format.
Like a [[Dictionaries|dictionary of dictionaries]].

- Curly braces denote one *object*
- Fields have a name in quotes, and a value after a colon
- The value of a field can be another *object*
- Arrays are denoted with `[]`

```json
{ 
	"fruit": "Apple", 
	"size": 3,
	"color": "Red",
	"states": {"Origin": "California", "Destination" : "Utah"},
	"dates":
	[
		{"picked":"02-05-1999", "shipped":"02-06-1999"},
		{"picked": "02-05-1999", "shipped": "02-06-1999"}
	]
}
```