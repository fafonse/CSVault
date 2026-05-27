## Math

### Functions
#### floor()
Rounds down to the nearest integer
```javascript
let f = 3.2;
f = Math.floor(f);
console.log(f);

// f = 3.0
```
#### random()
Returns a random *float* between 0 and 1.
```javascript
let r = Math.random();
// r = 0.4183
```

For using random for accessing random entries in an *array*, just multiply it by the length and use [[Standard Libraries#floor()|floor()]] to round it down.
```javascript
r = r * l.length;
r = Math.floor(r);

console.log(l[r]);
// Random list item
```