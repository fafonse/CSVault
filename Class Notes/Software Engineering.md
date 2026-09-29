## Code Standards
- Every method must have an XML comment
- Every member variable/attribute must have an XML comment
- Top of every class/file should have a header comment
- Properly formatted code/comments
- Complex code needs comments
- No repeated blocks of code
- No unnessecary logic
- No unnecessary complexity
- No non-private helper methods/member variables
- No debug/TODO/print statements in code

## Dependency maps
Have a [[Dictionaries|hashmap]] that has dependents as they key and who they depend on as their value.
- Now do it the other way around, dependencies as keys, those who need them as values

## Formula Delegates
Use [[Delegate|delegates]] for the lookup function for variables when evaluating formulas. For testing we can do a mock LookUp that just returns from a dictionary we have set for examples. Make sure that your formula class can handle the Lookup throwing an error.  

## Spreadsheet storage
We will store our cells using [[JSON]].
- A cell is inputted as a formula if it starts with `=`
- A cell is a number if it only contains a number
- A cell is a variable if identified as such
```json
"cells":
{
	"A1": {"textForm":"x"},
	"B1": {"textForm": "=5+5"}
}
```