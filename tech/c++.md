% c++ Tips

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

# emacs ide config #

* Jump to definition
* Auto-completion
* On-the-fly syntax highlighting
* Find file in project
* Compile with one key press
* Graphical debugger

# cmake #

## synopsis ##

``` shell
cmake [<options>] {<path-to-source> | <path-to-existing-build>}
cmake [<options>] -S <path-to-source> -B <path-to-build>
cmake [{-D <var>=<value>}...] -P <cmake-script-file>
cmake --build <dir> [<options>...] [-- <build-tool-options>...]
cmake --open <dir>
cmake -E <command> [<options>...]
cmake --find-package <options>...
```

## options ##
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

