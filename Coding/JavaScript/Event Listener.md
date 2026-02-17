A function that attaches an *event* part of the parent element to another function.


## Parameters
If reusing the same function with different parameters, you can't just inject the parameters normally. You instead need to make a wrapper function and call the desired function with your desired parameters.
```js
let redb = document.querySelector('#redbg');
let blueb = document.querySelector('#bluebg');
redb.onclick = () => {backgroundChange("red")};
blueb.onclick = () => {backgroundChange("blue")};
```