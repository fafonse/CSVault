### Margin
Your primary way of forcing elements away from each other. 
- `margin: [size];` - set margin
- There's also side specific variations:
	- `margin-right`, `margin-left`, `margin-up`, `margin-down`
### Padding
Your primary way of forcing elements closer together (not margin).
Also use to increase the "button" size of clickable links. Great for mobile accessibility.
- `padding: [size];` - set padding
- There's also side specific variations:
	- `padding-right`, `padding-left`, `padding-up`, `padding-down`
### Color
Sets the color of the text/element selected.
- `color: [color]` - set color
- You can input basically any form of color, there's even a couple built-ins that you can use with just a name
### Gap
Sets gaps between elements in a box/container, does NOT include the border. Use margin for that instead.
- `gap: [size]` - set gap

### Z-index
Sets the stacking order of elements. Higher values are displayed over lower ones. Only works on positioned elements.
- `z-index: [x]` - set z-index to $x$
	- You can use both negative and positive integers
	- There are also some keywords: `auto`, `inherit`, `initial`, `unset`
### Border
Adds a border to an element. Keep in mind that it surrounds the element, not the text. So double check element borders with the Inspect element.

Style can be *dashed*, *dotted*, or *solid*

- `border: [size] [style] [color];`

### Flex Container
Automatic grid/column grouping box. You can use it to automatically order elements evenly spaced out. Great for nav bars or other grid features.

- `display: flex` - Sets element to use display box
- `flex-direction` - aligns all changes on an axis
- `justify-content: [align];` - Moves content between `flex-end` and `flex-start`
	- Use `flex-end` and `flex-start` so it works no matter the `flex-direction`
	- `space-between` adds as much space between elements as possible, no border margin
	- `space-around` makes sure that there's space around elements (border included)
	- `space-even` equalizes space in between elements
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

### Grid
Puts elements in div in a procedural way.
- `display: grid` - sets display type to grid
- `grid-template-columns: [s1] [s2] [s...]` - Sets column sizes, each one's size needs to be declared
- `grid-template-rows: [s1] [s2] [s...]` - Sets row sizes
	- Use [[repeat]] for larger column/row amounts
	- Use `minmax(min, max)` to automatically size grids
		- `minmax(0px, auto)` is pretty good
- Use margins to add space between elements and the border
- Use [[CSS Tags#Gap|gap]] to add space only between grid elements
- Grid items without content don't display

#### Grid modifiers

- `grid-row: x/y` - sets the element into $(x,y)$ in the grid, with 1/1 being the top left
	- Messes up with the [[CSS Tags#Z-index|z-index]] and the order
	- If you're moving shit around, try to keep it in the associated order in HTML
		- Don't wanna mess with ordering bruh


>[!info] Floating Elements Above Grids
> 1. Create a new class for the element, and set it in the grid
> 2. Use `grid-column` or `grid-row` and set it to `span(x)`
> 	- $x$ in this case being the amount of grid squares you want to cover
> 	- Setting the span to the max length creates a new row/column
> 	- It will still span over the number you set, just modifies the grid to accommodate



# Special Tags/Modifiers
## Important
Forces the CSS to have priority over all else. Good for overwriting HTML CSS snippets, but you shouldn't really be doing that anyways.
 `css-tag: [param] !important`

>When you have too many `!important` modifiers, it can lead to *important wars*, where a majority of the CSS requires the modifier because you fucked up the CSS/HTML priority.

## Media Queries
Ask about the device, letting you determine a user's platform.
Works like an if statement, but a lot more sucky. 
Has higher priority only if its on the bottom the CSS or has a higher specificity.
#### code example
```css
@media (tag: param) {
	insert tags here
}
```

### Tags
- `hover` - Checks if the device can hover over stuff (mobile can't)
- `prefers-color-scheme` - Checks the user's preferred colors. Usually light or dark mode
- `max-width` - Width of the user's screen