An event that fires when something is changed, using *ChangedEventArgs* as the parameters.

```C#
private void ContentsChanged(ChangedEventArgs args)
{
	var data = arg?.Value ?? ""; // if arg is null, just set to ""
}
```