Refactoring is just rewriting code to be *cleaner* without changing the external functionality.
The best way of removing tech debt after its there. Never a bad time to do it really.

Benefits:
- Maintainability
	- Readability
	- Extensibility
	- Easier to Test
- Re-usability
	- Interfaces
	- Generic code
	- Clear functionality
- Performance
	- Efficient code
- Cost Reduction
	- Maintenance
	- Testing

### Examples
- Using a variable for some super long one-liner
	- `int height = myWindow.xwindow.getHeight()`
	- Makes it easier to debug/test by replacing values
- Renaming variables
	- Keep it consistent with camel case/snake case/whatever
	- Great use case for AI, it tends to have good variable names
- Merging functions
	- Don't repeat yourself
	- Ensures that the bugs all stay in one place