# Bashy
https://www.urbandictionary.com/define.php?term=bashy

Bashy is scripting environment for user-friendly scripts.
It is also a declaration of some new conventions and practices in shell scripting.

Bashy-core.zip contains the minimun set of files, the platform to build scripts on. Few additional scripts are added for demonstration and inspiration.
Scripts are installed under user's home and root access is not required. I have avoided external commands as much as possible so Bashy should be quite portable.

Any ideas and help to support the world conquest are welcome :).

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
1. Extract the package in your home folder with unzip
2. Run **~/.config/bashy/install.sh** or manually add 'source .config/bashyrc' to you .bashrc file
3. Run **source ~/.config/bashyrc** (or relogin).

## Content
### Mandatory login script
    .config/bashyrc
      Source this from ~/.bashrc or let 'bashy install' to install the hook.
### Mandatory source files
    .local/bin/bashy.bash
      Bashy basic environment and functions.

    .local/bin/complete.bash
      Functions for command line completion.

    .local/bin/setopt.bash
      Functions for command line option handling.

    .local/bin/validate.bash
      Generic functions for datatype validation used also by setopt.bash.
### Essential executables
    .local/bin/bashy
      Companion tool for help and templates for scripts and libraries.

    .local/bin/bashy-logadm
    .local/bin/bashy-logs
      View and manage Bashy logs

    .config/bashy/install.sh
      Install or uninstall Bashy hook in ~/.bashrc
### Extras for demostration and inspiration
    .local/bin/color.bash
      Functions for terminal colors. Not mandatory but will be automatically used for error prompts etc. if found.

    .local/bin/color-cubes
    .config/color/color-names
      Demo script providing some information on terminal colors.
      Enable 256 colors in your terminal to see all color patterns.

    .local/bin/array.bash
      Functions for array manipulation

    .local/bin/input.bash
      Functions to prompt for user input

    .local/bin/bunique.bash
      Functions for temporary files with automatic cleanup

    .local/bin/ppcsv
    .local/bin/csv.bash
      Functions for comma-separated data and a 'pritty-print' script for demonstration.

    .local/bin/mutex.bash
      Functions for mutual exclusion

    .local/bin/search
    .config/search/defaults.setopt
      Search'n'replace tool with extensive set of command line options.
      Modify default options to your needs.

    .local/bin/viconfig
      Demonstrates command completion to help editing files under ~/.config
## Helpful commands
    bashy help [ __library__.bash ]
      for help on function libraries in ~/bin. or main library bashy.bash if argument is omitted.

    bashy sekelton-with-comments [ __filename__ ]
    bashyrc.complete-refresh
      Create you first script skeleton with comments in ~/bin
      Run bashyrc.complete-refresh to add a compspec for the command in current shell

    <command> --help
      All scripts document themselves. Help option is built-in.

    bashyrc.help
      function for help on login scripts and configuration
## Dependencies and requirements
Bash 4.4 required, tested also with 5.2.
Path ~/.local/bin must be in $PATH.
## Author
https://github.com/jounihenrikki/bashy/
[Jouni Henrikki Vääriskoski](mailto:?to=jouni.vaariskoski@gmail.com&subject=Bashy&body=Hello%20Jouni,)
Work is under GNU General Public License [GPLv3](https://www.gnu.org/licenses/gpl-3.0.html)
