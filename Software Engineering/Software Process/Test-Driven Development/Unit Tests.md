Code that tests a single function/method.

Should be small, fast, self-contained, and specific. You should also name them in a way that is easily readable ([an example from microsoft](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices)).

## Private methods
Private methods can't be directly invoked from the test class.

However...
- Test them *indirectly*, use public methods that call them.
- If you can't get 100% coverage of your private methods through public means, you have *shit code*