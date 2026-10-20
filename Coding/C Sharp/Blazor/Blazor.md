HTML and C# entwined a goofy ass format. Directly edit and call HTML from within the HTML, and render the website server-side.

```C#
<PageTitle>Home</PageTitle>

@{
	if (showInfo)
	{
		<p>blah blah show info</p>
	}
}

@code {
// add code
}
```
