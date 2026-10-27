Lets us define a variable type for a method.

```C#
delegate int Comparator(int i1, int i2);
// Comparator is now a type

public static int DoSomething(int i1, int i2) {
 // ...
}

Comparator cmp = DoSomething;
```

## Examples

### Filtering
You can use delegates as a "generic" container for logic. Here we can easily replace and insert filtering logic into our validation method. 

```C#
delegate bool StudentFilter(Student s); // create filter type

public static bool GPAFilter(Student s) { ... }
public static bool GradeFilter(Student s) { ... }


public List<student> ValidateStudents(List<Student> studentList, StudentFilter filter)
{
	List<Student> valid_students = new List<Student>;
	foreach (Student s in studentList)
	{
		if (filter(s))
		{
			valid_students.Add(s)
		}	
	}
	return valid_students;
}

ValidateStudents(studentList, GPAFilter);
ValidateStudents(studentList, GradeFilter);
```