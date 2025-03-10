# Bashy
https://www.urbandictionary.com/define.php?term=bashy

Bashy is scripting environment for user-friendly scripts.
It is also a declaration of some new conventions and practices in shell scripting.

Bashy.zip contains the minimun set of files, the "platform" to build scripts on. Additional zip packages add command line completion, ANSI color support and logging.
Scripts are installed under user's home and root access is not required. I have avoided external commands as much as possible so Bashy should be quite portable.

## Features
### Long command line options
Long command line options with strongly typed and validated option arguments parsed in normal getopts loop. Common options like --help are built-in.

### Command completion
Instant completion for command line options, option arguments and positional parameters. No configuration outside scripts is needed.

### Error handling
Best practices for error handling. Bash ERR pseudo signal can trigger backtrace for debugging.

### Logging
Functions for logging and tools for log housekeeping. All script invocations are logged by default.

### Debugging
Generic --debug= command line option. Debug options can be registered in library source files or scripts.

### Housekeeping
EXIT pseudo signal is trapped for cleanup functions. Script or library can register functions to be run on exit.

### Custom libraries
Scripts can source additional libraries together with main library bashy.bash. A template is provided.

### Fast script creation
Scripts and function libraries can be easily created using skeletons.

### Support for multiple configuration paths
Inspired by 'XDG Base Directory Specification', multiple configuration base paths are supported

## Installation
1. Download zip files to you home folder and unzip bashy.zip
2. For command completion, unzip bashy-complete.zip (optional)
3. For ANSI color support, unzip bashy-color.zip (optional)
4. For logging, unzip bashy-log.zip (optional)
5. Run **~/.config/bashy/install.sh** or manually add 'source .config/bashyrc' to you .bashrc file
6. Run **source ~/.config/bashyrc** (or relogin).

## To get help
    bashy help [ <library>.bash ]
      for help on function libraries in ~/bin. or main library bashy.bash if argument is omitted.

    bashy sekelton-with-comments [ <filename> ]
      Create you first script skeleton with comments in ~/bin

    <command> --help
      All scripts document themselves. Help option is built-in.

    bashyrc.help
        Help on functions for interactive use
## Content in bashy.zip
    .local/bin/bashy
      Tool for help and templates for scripts and libraries.

    .local/bin/bashy.bash
    .local/bin/setopt.bash
    .local/bin/validate.bash
    .local/bin/input.bash
      Source files with functions for basic stuff, command line options, datatype validation and user input.

    .config/bashyrc
      Source this from ~/.bashrc or let 'bashy install' to install the hook.

    .config/bashy/*
      Install script and configuration for .local/bin/bashy
### Files in bashy-complete.zip
    .local/bin/complete.bash
      Functions for command line completion.

    .config/bashyrc.d/0bashyrc-complete.bash
      Initializes command completion on logon. Automatically sourced by .config/bashyrc
### Files in bashy-log.zip
    .local/bin/bashy-logadm
    .local/bin/bashy-logs
      View and manage Bashy logs

    .local/bin/log.bash
      Adds logging to scripts
## Files in bashy-color.bash
    .local/bin/color.bash
      Functions for ANSI colors. Will be automatically sourced and used by bashy.error() etc. when found.

    .local/bin/color-cubes
    .config/color/color-names
      Script providing some information on terminal colors.
      Enable 256 colors in your terminal to see all color patterns.
## Dependencies and requirements
Bash 4.4 required, tested also with 5.2.
Path ~/.local/bin must be in $PATH.
## Author
https://github.com/jounihenrikki/bashy/
Work is under GNU General Public License [GPLv3](https://www.gnu.org/licenses/gpl-3.0.html)
