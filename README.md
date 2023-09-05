# Table of Contents

- [Introduction](#introduction)
- [dcc!](#dcc)
- [spim!](#spim)
- [format!](#format)
- [Installation](#installation)


# Introduction
Collection of shell scripts made by yours truly. 

**Note:** these scripts are written for Linux, and may not work on macOS or Windows.


# dcc!
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






# spim!
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





# format!
Aims to quickly format .c (and .cpp?) files with `clang-format`. Usage:
```bash
format!
```
Formats the most recently edited .c file in the directory `~/_` (can be changed in the script).

```bash
format! <filename>
```
Formats the specified .c file.






# Installation

In Unix-like operating systems such as Linux and macOS, you can "install" a shell script so that it's available from any directory in the terminal, allowing you to run it like any other command-line program. Here are some ways to do that:

### Method 1: Add Script to a Directory in Your PATH

1. **Make Your Script Executable:** First, make sure that your script is executable. You can make it executable by running:
    ```bash
    chmod +x /path/to/your_script.sh
    ```

2. **Move Script to `PATH`:** Move your script to one of the directories listed in your `$PATH` environment variable.
    ```bash
    mv /path/to/your_script.sh /usr/local/bin/
    ```
   or, you could create a symlink instead:
    ```bash
    ln -s /path/to/your_script.sh /usr/local/bin/your_script
    ```
   
3. **Check Availability:** Open a new terminal window and you should be able to run `your_script` (or `your_script.sh` depending on how you named it) from any directory.

### Method 2: Add Script Directory to PATH

1. **Make Your Script Executable:**
    ```bash
    chmod +x /path/to/your_script.sh
    ```

2. **Add to PATH:** Add the directory containing your script to the `$PATH` variable. You can put the following line in your `.bashrc`, `.zshrc`, or whatever shell configuration file you're using:
    ```bash
    export PATH=$PATH:/path/to/
    ```
   Don't forget to source the file or open a new terminal window to make sure the changes take effect:
    ```bash
    source ~/.bashrc  # or source ~/.zshrc
    ```

### Method 3: Alias

1. **Create Alias:** If you don't want to move your script, you can create an alias in your shell configuration file (`.bashrc`, `.zshrc`, etc.):
    ```bash
    alias your_script="/path/to/your_script.sh"
    ```
   Then, `source` your shell configuration file:
    ```bash
    source ~/.bashrc  # or source ~/.zshrc
    ```

2. **Check Availability:** Now, you should be able to run `your_script` as a command.

Choose a method that best suits your needs!