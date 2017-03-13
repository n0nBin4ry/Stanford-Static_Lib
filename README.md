# Stanford-Static_Lib
Practiced making a Static Library using the Stanford C++ Library as the source

###Motiviation: 
To make Staford C++ Library easier to use/access (in my opinion) and learn/practice how to make/use static libraries.

###TO-DO:
- Keep testing MinGW and MinGW-w64 static libraries.
- Seek help on undefined reference to 'stacktrace::call_stack::call_stack' in exceptions 
- Look into shared libraries and how to build those, will either add them to this repo or another.
- Spell-check Readme file

###LOG: (and personal notes)
- 3/7/17:
  - Put all .cpp files into src directory and all .h files into include directory (but kept the headers in private within their 
	directory but moved it into the include directory).
- 3/8/17:
	- For MinGW: Learned I need to include the flag -std=c++11 (or -std=gnu++11) in command line when making an object(.o) file. So
	  far now my command for building objects is: g++ -I.\include -c file.cpp -std=c++11 (while in the src directory)
	- For MinGW: learned that I needed strsafe.h in the main include folder of MinGW when making an object file out of call_stack_gcc.cpp,
		didn't have it for some reason. Downloaded it from github somewhere and set put it where it needs to go.
	- Recieved many more errors; going to try to comment out the inclusion of strsafe.h in call_stack_gc.cpp.
	- Compiled call_stack_gcc.o without a problem, for now.
	- Similar problem occured for call_stack_windows.cpp, but the missing header is dgbhelp.h
	- Couldn't find the right file online. Going to try commenting out the inclusion of dgbhelp.h
	- Couldn't work still, deciding to exclude call_stack_windows.cpp for now and moving on.
	- Wishful-Thinking: Maybe call_stack_windows.cpp is only needed when using VS? So maybe no need if using MinGW or Cygwin?
	- No more errors when making rest of object files. (maybe my wishful thinking was correct)
	- Put all object files in the objects directory that's at the root of this repository.
	- Made a Makefile for building the static library. Named static library: stanlib.a
	- Might be too early to shout success, but will test tomorrow
- 3/9/17
	- learned I need to prefix every static library file with "lib" so I renamed the static library to libStanford.a
	- Made a main file to test library but got some errors, but when I use same main file with the regular source files I get the same
		error so maybe its just my main file, will keep trying to test it.
- 3/10/17
	- Someone suggested I use MinGW-w64 since I have a 64bit machine. I know that MinGW and MinGW-w64 are 2 completely different projects
		at this point and that MinGW can be used on 64bit machines; tried explaining this but they insited I try anyways. I might as well
		compare the two for myself.
	- Set up MinGW-w64 (put bin path in enviromental variables and removed MinGW's bin path).
	- Tried building static file, but learned I need to recompile the object files using MinGW-w64 since MinGW object files can't be used
		by MinGW-w64 and vice versa.
	- Exact same command as MinGW for making the objects, but didn't need to add the -std=c++11 or -std=gnu++11 flag.
	- Using MinGW-w64: When I got to compiling call_stack_windows.cpp, I got errors suggesting there are 3 typos in the file, and there
		were. Fixed them and tried again. It worked.
	- Using MinGW: Also didn't need to comment out inclusion of strsafe.h in call_stack_gcc.cpp
	- MinGW-w64 returns compiler warning (when making object from hashcode.cpp) that type casting from void to long int loses precision.
		So flags -w and -fpermissive needed to ignore warning and compile. Compiles fine.
	- Rest of objects compiled without problem.
	- Split MinGW and MinGW-w64 object files into two seperate directories within the objects directory.
	- Used same Makefile I used to compile MinGW-w64 static library to make MinGW-w64 static library but named it libStanford64.a
	- Split MinGW and MinGW-w64 static library files into two seperate directories within the libs directory.
	- Using test files given by professor to test library, but most of them came back with an error of reaching an undeclared function
		called closeConsoleAndExit(). Tried to use test files without static library and using the source files instead.. Led to many more
		errors.
	- Maybe the error is because of the test file and not the static library.
- 3/11/17
	- Put MinGW-w64 changes onto GitHub repository, then but notes from notebook onto readme.
- 3/12/17
	- Found out by author of test files that the closeConsoleAndExist function is only in his personal version of the Library so I just
		need to comment it out.
	- Now I get and error that says there is undefined reference to 'stacktrace::call_stack::call_stack' 3 seperate times within
		exception.o which is basically just exception.cpp
