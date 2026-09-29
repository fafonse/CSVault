The built-in [[JSON]] [[Serializing|serializer]] for C#. 

- Includes public fields by default
	- Include privates using `[JsonInclude]`
	- Ignore fields with `[JsonIgnore]`
- Requires a default constructor for created classes to work
- Change the field name with `[JsonProperty]`


```c#
// Saving and loading an object instance in C#
Student t = new Student("blah blah blah");
string message = JsonSerializer.Serialize(t);

Student t_copy = JsonSerializer.deserialize<Student>(message);
```