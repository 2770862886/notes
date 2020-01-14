% c++ Tips

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

[Modern C++](https://github.com/changkun/modern-cpp-tutorial/releases)  
[llvm](http://llvm.org/)  
[lsp-mode config](https://www.mortens.dev/blog/emacs-and-the-language-server-protocol/)  
[Debugging with GDB](https://sourceware.org/gdb/onlinedocs/gdb/index.html)  
[libuv](https://github.com/luohaha/Chinese-uvbook)  
[跟我一起写Makefile](https://seisman.github.io/how-to-write-makefile/introduction.html)  

emacs config
============

* Jump to definition
* Auto-completion
* On-the-fly syntax highlighting
* Find file in project
* Compile with one key press
* Graphical debugger
y

# Essential C++ #

## Basics C++ Programming ##

### 对象的定义与初始化 ###

``` c++
#include <string>

string user_name;
int num_tries(0);
complex<double> purei(0, 7);

```


## Procedural Programming ##

## Generic Programming ##

## Object-Based Programming ##

## Object-Oriented Programming ##

## Programming with Templates ##

## Exception Handling ##

debug
=====

synopsis
--------

``` shell
cmake [<options>] {<path-to-source> | <path-to-existing-build>}
cmake [<options>] -S <path-to-source> -B <path-to-build>
cmake [{-D <var>=<value>}...] -P <cmake-script-file>
cmake --build <dir> [<options>...] [-- <build-tool-options>...]
cmake --open <dir>
cmake -E <command> [<options>...]
cmake --find-package <options>...
```

options
-------

|                     |                                                                              |
|---------------------|------------------------------------------------------------------------------|
| -S <path-to-source> | Path to root directory of the CMake project to build.                        |
| -B <path-to-build>  | Path to root directory of the CMake will use as the root of build directory. |
|                     | If the directory doesn't already exist CMake will make it.                   |
| -C <initial-cache>  | Pre-load a script to populate the cache.                                     |
|                     |                                                                              |

## Build Tool Mode ##

## Command-Line Tool Mode ##

# object model #

# performance #

