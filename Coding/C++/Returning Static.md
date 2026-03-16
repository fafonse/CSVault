Sometimes you have cases where you return a reference to a static variable. When you do that, you can't return a const, but you require that its always returning the same thing.

It's important to note that static variables that change for one function, change in all functions. In the example below, if it returns the error color, the caller can change the error to whatever they want, and all future `[]` calls will return that changed color.

```cpp
Color& operator[] (const int &i) {
	if (i < 0 || i >= (int)colors.size()) { // if out of range...
		static Color error_color(-1, -1, -1); // runs once
		error_color = Color(-1, -1, -1); // reassignment
		return error_color;	
	}
	return colors[i];
}

colors = new Color[11];
Color c = colors[12];

```