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