# shell_scripts
Collection of shell scripts made by yours truly. 

**Note:** these scripts are written for Linux, and may not work on macOS and Windows.

## dcc!
Aims to simplify the build-and-run process of 'toy' to medium sized C programs, like `fibonacci.c`, `cs_bookshelf.c`, etc. 

The script properly handles warnings and errors from `dcc` and preserves `dcc`'s text formatting.

The script can be used in two ways:

```bash
dcc!
```
This will build an executable from the most recently edited `.c` file in the directory and its subdirectories using `dcc`, then run and delete it. The directory to search is set to `~/_` by default and can be changed by modifying the script. 

```bash
dcc! <file_name> <params>
```
This will perform the build, run, and delete process for the file specified by `file_name` with the specified `params`. Note that output arguments ("`-o <word>`") are ignored.



## spim!
Aims to simplify the `spim` command and hide the text overhead it produces. Specifically, it removes the text:
```
SPIM Version 8.0 of January 8, 2010
Copyright 1990-2010, James R. Larus.
All Rights Reserved.
See the file README for a full copyright notice.
Loaded: /usr/lib/spim/exceptions.s
```

The script can be used in two ways:
```bash
spim!
```
This will find the most recently edited `.asm` or `.s` file in the `~/_` directory (which can be changed by modifying the script) and its subdirectory, and simulate it with `spim`.

```bash
spim! <file_name> <params>
```
This will simulate the given `file_name` file with the given `params` with spim.