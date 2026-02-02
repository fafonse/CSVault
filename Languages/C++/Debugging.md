To debug your C++ code, the process has a couple steps.

First you have to set a *breakpoint* if you'd like. On Astro Vim you can access all the debug commands with `Leader + d`.

After you have your debug flags in your file, you then need to *save* the file and then compile with the debug flag. For g++ it's the `-g` flag.
- `g++ -g hello.cpp -o hello.out`

Then after compiling you then need to open the debugger and select the *compiled executable*. Then the debugger can properly go through step by step.