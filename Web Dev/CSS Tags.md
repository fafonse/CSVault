### Margin
Your primary way of forcing elements away from each other. You can use pixels, em, rem, whatever.
`margin: [size];`
### Border
Adds a border to an element. Keep in mind that it surrounds the element, not the text. So double check element borders with the Inspect element.

Style can be *dashed*, *dotted*, or *solid*

`border: [size] [style] [color];`

### Flex Container
Automatic grid/column grouping box. You can use it to automatically order elements evenly spaced out. Great for nav bars or other grid features.

- `display: flex` - Sets element to use display box
- `flex-direction`
- `justify-content: [align];` - Moves content between `flex-end` and `flex-start`
	- Use `flex-end` and `flex-start` so it works no matter the `flex-direction`
	- `space-between` adds as much space between elements as possible, no border margin
	- `space-around` makes sure that there's space around elements (border included)
	- `space-even` 
- `align-items: [align];` - aligns the against the flex direction

### Float
Floats elements over others. Think of it of just smacking the element wherever you want. 
- `float: [direction]` - set float

### Transition
Add lerp to any tag, use with pseudo selectors to smooth out any interactions.

- `transition: [tag] [time] [easing style]`
	- Add a transition/lerp to a tag
	- Time is how long it takes to transition
	- Easing styles can be `ease-in-out`, `bounce`

### Transform
Transform your elements, with size/rotation/translation.

- `transform: [transforms]` - scale/rotate your element
	- `scale(x)` - size by a factor