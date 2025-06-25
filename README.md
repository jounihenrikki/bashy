# Bashy
https://www.urbandictionary.com/define.php?term=bashy

Bashy is private scripting environment and toolkit for developer- and user-friendly scripting.
It is also a declaration of some new conventions and practices in shell scripting.

Bashy is written in Bash.
It can be easily deployed in isolated environments and further propagated to other hosts and users.
I have avoided external dependencies as much as possible so Bashy should be quite portable.
Bash 4.4 or higher is required.

Bashy.zip contains the minimun set of files to build scripts on. Additional zip packages add command line completion, ANSI color support, logging and more.
Scripts are installed under user's home and root access is not required.

## Features
### Long command line options
Long command line options with strongly typed and validated option arguments parsed in normal getopts loop. Common options like --help are built-in.

### Command completion
Long command options are powerful but hard to remember. Package 'complete' adds completion for command line options, enumerated option arguments and positional parameters. No configuration outside main script is needed.

### Error handling
Best practices for error handling. Bash ERR pseudo signal can trigger backtrace for debugging.

### Logging
Log database, functions for logging and tools for housekeeping. All script invocations are logged by default.

### Debugging
Generic --debug= command line option. Debug options can be registered in library source files or scripts.

### Housekeeping
EXIT pseudo signal is trapped for cleanup functions. Script or library can register functions to be run on exit.

### Fast script creation
Scripts and function libraries can be easily created using skeletons.

### ANDI color support
With 'color' package you see Bashy error messages and command/libary help in color. And of course have possibility to add color in any script.

### Support for multiple configuration paths
Like 'XDG Base Directory Specification', Bashy support multiple configuration paths. Configurations are read from first matching location.

## To install
1. Copy zip files to you home folder
2. Unzip bashy.zip
3. Unzip bashy-complete.zip for command completion (optional but highly recommended)
4. Unzip bashy-color.zip for ANSI color support (optional)
5. Unzip bashy-log.zip for logging (optional)
6. Run **~/.config/bashy/install.sh** or manually add 'source .config/bashyrc' to ~/.bashrc file
7. Run **source ~/.config/bashyrc** or relogin.

## To uninstall
1. Uninstall supplemental packages (not 'bashy'): **bashy uninstall <package>**
2. Remove the hook from ~/.bashyrc: **~/.config/bashy/install.sh -u**
3. Uninstall base package: bashy uninstall bashy
4. If you had installed log package, remove logs: **rm -rf ~/.local/state/bashy-logs**

## To propagate set of packages to another user
1. Pack a collection of packages: **bashy package bashy <package> ...**
2. Copy: **scp bundle.zip <login>:**
3. Unzip: **ssh <login> unzip bundle.zip**
4. Install: **ssh <login> .config/bashy/install.sh**

## To get help
    bashy help [ <library>.bash ]
      for help on function libraries in ~/bin. or main library bashy.bash if argument is omitted.

    bashy sekelton-with-comments [ <filename> ]
      Create you first script skeleton with comments in ~/bin

    <command> --help
      All scripts document themselves. Help option is built-in.

    bashyrc.help
        Help on functions for interactive use
## File content
### bashy.zip
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
### bashy-complete.zip
    .local/bin/complete.bash
      Functions for command line completion.

    .config/bashyrc.d/0bashyrc-complete.bash
      Initializes command completion on logon. Automatically sourced by .config/bashyrc
### bashy-log.zip
    .local/bin/bashy-logadm
    .local/bin/bashy-logs
      View and manage Bashy logs

    .local/bin/log.bash
      Adds logging to scripts
### bashy-color.bash
    .local/bin/color.bash
      Functions for ANSI colors. Will be automatically sourced and used by bashy.error() etc. when found.

    .local/bin/color-cubes
    .config/color/color-names
      Script providing some information on terminal colors.
      Enable 256 colors in your terminal to see all color patterns.
### bashy-util.bash
    Collection of scripts and libraries yet to be documented here. Use 'bashy help' or --help to learn more.
## Author
https://github.com/jounihenrikki/bashy/
Work is under GNU General Public License [GPLv3](https://www.gnu.org/licenses/gpl-3.0.html)
