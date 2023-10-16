# Table of Contents

- [Introduction](#introduction)
- [cse](#cse)
- [dcc!](#dcc)
- [mipsy!](#mipsy)
- [spim!](#spim)
- [format!](#format)
- [Installation](#installation)


# Introduction
Collection of shell scripts made by yours truly. 

**Note:** these scripts are written for Linux, and may not work on macOS or Windows.


# cse

## Overview:
This script facilitates synchronization and interaction with remote systems, specifically tailored for the CSE environment at UNSW. It provides capabilities to:
- SSH into the remote system based on the user's current directory.
- Sync files from the remote system to the local system (get).
- Sync files from the local system to the remote system (set).
- Execute arbitrary commands on the remote system.

## Prerequisites:
- Ensure you have `ssh` and `rsync` installed on your machine.
- The script assumes a specific naming convention for the host, based on the user's ID.

## Usage:

### 1. SSH:
Simply run the script without any arguments:
```sh
cse
```
This will SSH you into the remote CSE machine. If your current directory matches the local path (by default `$HOME/Code/cse`), the script will attempt to navigate you to the corresponding directory on the remote.

### 2. Synchronization:
The script uses `rsync` for synchronization. The following options are available:

- **get** : Syncs files from the remote system to the local machine.
  ```sh
  cse get
  ```
  It performs a dry run first and asks for user confirmation before actual sync.

- **set** : Syncs files from the local machine to the remote system.
  ```sh
  cse set
  ```
  This operation doesn't delete files on the remote. Similar to 'get', it performs a dry run and asks for user confirmation.

### 3. Execute Commands:
To run a command on the remote system:
```sh
cse [COMMAND]
```
Where `[COMMAND]` is any command you wish to run on the remote system. If your current directory matches the local path, the script will attempt to execute the command in the corresponding directory on the remote.

## Notes:

- The script excludes certain directories by default during sync operations. These are: `gitlab/`, `github/`, and `node_modules/`. Modify the `exclude_args` array if you want to change this behavior.
  
# dcc!
Simplifies the build-and-run process C programs. The script properly handles warnings and errors from `dcc` and preserves `dcc`'s text formatting.

Note that `dcc!` does not run the produced executable if `dcc` outputs a warning.

The script can be used like such:

```bash
dcc! <file> <dcc_args> :: <executable_args>
```

If `<file>` is not provided, `dcc!` will run with the most recently edited `.c` file in the `~/_` directory and its subdirectories. You can change this setting by modifying the script.

If `<dcc_args>` are provided, they will be passed to `dcc` except for `-o` arguments.

If `:: <executable_args>` are provided, they will be passed to the executable.


# mipsy!
Simplifies the `mipsy` command. The script's usage is defined as:

```bash
mipsy! <file> <args>
```

If `<file>` is not provided, `mipsy!` will run the most recently edited `.asm` or `.s` file in the `~/_` directory and its subdirectories. You can change this setting by modifying the script.

If `<args>` are provided, they will be passed to `mipsy`.


# spim!
Simplifies the `spim` command. The script's usage is defined as:
```bash
spim! <file> <args> 
```

If `<file>` is not provided, `mipsy!` will run with the most recently edited `.asm` or `.s` file in the `~/_` directory and its subdirectories. You can change this setting by modifying the script.

If `<args>` are provided, they will be passed to `spim`.


# format!
Quickly formats .c (and .cpp?), .s, and .asm files using `clang-format` and [mips_formatter](https://github.com/Chinosu/mips_formatter). Usage:
```bash
format! <file>
```
If `<file>` is not provided, `format!` will format the most recently edited .c, .s, or .asm file in the directory `~/_` and its subdirectories. You can change this setting by modifying the script.

**Note:** `format!` assumes that [mips_formatter](https://github.com/Chinosu/mips_formatter) is located like such:

```
parent/
├─ mips_formatter/
│  ├─ main.py
│  ├─ ...
├─ shell_scripts/
│  ├─ format!
│  ├─ ...
```
You can modify this in `format!` if you want.




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
