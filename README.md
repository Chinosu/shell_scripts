# Table of Contents

- [Introduction](#introduction)
- [dcc!](#dcc)
- [mipsy!](#mipsy)
- [spim!](#spim)
- [format!](#format)
- [Installation](#installation)


# Introduction
Collection of shell scripts made by yours truly. 

**Note:** these scripts are written for Linux, and may not work on macOS or Windows.


# dcc!
Simplifies the build-and-run process C programs. The script properly handles warnings and errors from `dcc` and preserves `dcc`'s text formatting.

Note that `dcc!` does not run the produced executable if `dcc` outputs a warning.

The script can be used like such:

```bash
dcc! <file> <params>
```

If `<file>` is not provided, `dcc!` will run with the most recently edited `.c` file in the `~/_` directory and its subdirectories. You can change this setting by modifying the script.

If `<params>` are provided, they will be passed to `dcc` except for `-o` arguments.


# mipsy!
Simplifies the `mipsy` command. The script's usage is defined as:

```bash
mipsy! <file> <params>
```

If `<file>` is not provided, `mipsy!` will run the most recently edited `.asm` or `.s` file in the `~/_` directory and its subdirectories. You can change this setting by modifying the script.

If `<params>` are provided, they will be passed to `mipsy`.


# spim!
Simplifies the `spim` command. The script's usage is defined as:
```bash
spim! <file> <params> 
```

If `<file>` is not provided, `mipsy!` will run with the most recently edited `.asm` or `.s` file in the `~/_` directory and its subdirectories. You can change this setting by modifying the script.

If `<params>` are provided, they will be passed to `spim`.


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
