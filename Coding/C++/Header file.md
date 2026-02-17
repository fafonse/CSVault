A public declaration of functions and stuff inside your program.
Any libraries you `#include` in your header file don't need to be included in any other files that use that header file.
## Example
```c++
#ifndef IMAGE_MENU_H // check if it's defined

#define IMAGE_MENU_H

#include <string>
#include <iostream>

std::string getString( std::istream& is, std::ostream& os, const std::string& prompt );
int getInteger( std::istream& is, std::ostream& os, const std::string& prompt );
double getDouble( std::istream& is, std::ostream& os, const std::string& prompt );
int askQuestions3(std::istream& is, std::ostream& os);
int assignment1( std::istream& is, std::ostream& os );

#endif // remember to end your definition
```

## Guard

Special instructions that run pre-compile. They tell your compiler what to do when it sees your header file.
### Pragma and ifndef

When compiling your code you need to compile header files only **once**.
There are two main ways of doing it:
- Pragma
	- `#pragma once` compiles the header once
- ifndef, def, and endef
	- Checks if your code is *not defined*, if so it *defines it*, then it *ends* the definition

```cpp
#pragma once

code here...
```

```cpp
#ifndef EXAMPLE_H
#def EXAMPLE_H

code here...
#endef
```