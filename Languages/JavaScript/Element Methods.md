## Unordered List

### appendChild()
Appends a `<li>` to the `<ul>`.

```javascript
let ul = document.querySelector('ul');

let li = document.createElement('li');
ul.appendChild(li);
li.innerHTML = "Wassup!!!"

// - LI 1
// - LI 2
// - Wassup!!!
```