# physicell_cmake

Just as the name states, we're trying to demonstrate the basics of using cmake for a project.

* Install CMake https://cmake.org/download

* Clone or download/extract the .zip for this repo. 

## On OSX/Linux:
```
$ cd <path-to-repo>
$ mkdir build
$ cd build
$ cmake ..
```
or if you want to specify different compilers than the default (e.g., on OSX, we used [brew to install a modern version of gcc that had OpenMP](http://www.mathcancer.org/blog/setting-up-gcc-openmp-on-osx-homebrew-edition/)):
```
$ cmake -DCMAKE_CXX_COMPILER=g++-11 -DCMAKE_C_COMPILER=gcc-11 ..
```
Assuming the cmake is successful, try to build it:
```
$ make
# or if you encounter build errors, try:
$ make VERBOSE=1
```
Assuming it builds successfully, copy/run the executable from the root:
```
$ cp template ..
$ cd ..
$ ./template
```

## On Windows 10: 

Provide options here, depending on what a user currently has installed and how minimal of an installation they would like (since we only need an OpenMP-enabled C++ compiler).

Install C++: https://docs.microsoft.com/en-us/cpp/build/vscpp-step-0-installation?view=vs-2019

<b>Previous instructions</b> Install [Visual Studio](https://www.visualstudio.com/downloads/) (I use the free Community edition). After this is successfully installed, open a Command Prompt shell (or PowerShell) and:
<!--
I run a batch script (.bat) as follows:
```
cmd.exe /k ""c:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat" x64 & powershell"
```
which seems to do some magic of making my Command Prompt shell know about the VS17 "cl" compiler (and put my Command Prompt into "Powershell" mode so I'll have more Unix-like commands). Then I run:
-->
```
PS C:<path-to-repo> mkdir build
PS C:<path-to-repo> cd build
PS C:<path-to-repo>\build> cmake ..
  ... this will generate files for the Visual Studio compiler; hopefully no errors.
  
PS C:<path-to-repo>\build> cmake --build . --config Release
  ... this will attempt to compile & build the executable.
```
Assuming it builds successfully, run the executable from a new subfolder:
```
PS C:<path-to-repo>\build> mkdir run1
PS C:<path-to-repo>\build> cd run1
PS C:<path-to-repo>\build\run1> ..\Release\PhysiCell.exe
```

