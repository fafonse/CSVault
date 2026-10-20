Sort of like a id for an HTML element, but in code.
Typically elements in Blazor don't have any names or anything, so this is what you do to refer to them.

```C#
private ElementReference ContentsBox; // create the thing

<input @bind=.../>
<input @ref="ContentsBox"/>

private void CellClicked(int row, int col)
{
	SelectedCell = row + ", " + col; 
	ContentsBox.FocusAsync(); // refer to the bo as before
}
```