
## Attributes
### Length
Returns an `int` value of the length of the array.
```javascript
const letters = ["A", "B", "C"]
console.log(letters.length)
```
## Basic Functions


## Join (toString)
Joins array elements together into a string.
```javascript
const letters = ["A", "B", "C"] ```
```

## forEach()
Runs a function for each element while passing the elements to the function
```javascript
const hobbies = ["games", "sports", "coding"];

function shoutHobby(item) {
	console.log("I love " + item, "!\n");
}

hobbies.forEach(shoutHobby);

// I love games!
// I love sports!
// I love coding!
```