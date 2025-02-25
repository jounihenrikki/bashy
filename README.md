# Bashy
https://www.urbandictionary.com/define.php?term=bashy

Bashy is scripting environment for user-friendly scripts.
It is also a declaration of new conventions and look-and-feel in shell scripting.

Long command line options and command completion are the most useful features and the soul of Bashy, so look into those first.

Bashy-core.zip contains the minimun set of files, the platform to build scripts on. Few additional scripts are added for demonstration and inspiration.
Scripts are installed under user's home and root access is not required. I have avoided external commands as much as possible so Bashy should be quite portable.

Your new scripts are created using a template which provides all you need to start with.

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
Example: create script skeleton ~/bin/myscript and add a compspec for the current shell:

  bashy skeleton myscript; bashyrc.complete-refresh

## Installation
1. Extract the package to your home folder with unzip
2. Run **~/.config/bashy/install.sh** or manually add 'source .config/bashyrc' to you .bashrc file
3. Run **source ~/.config/bashyrc** (or relogin).

## Content
### Mandatory login script
    .config/bashyrc
      Source this from ~/.bashrc or let 'bashy install' to install the hook.
      Once sourced, some help can be printed with bashyrc.help command.
### Mandatory source files
    .local/bin/bashy.bash
      Bashy basic environment and functions

    .local/bin/complete.bash
      Functions for command line completion

    .local/bin/setopt.bash
      Functions for command line option handling

    .local/bin/validate.bash
      Functions for datatytpe validation, used by setopt.bash
### Essential executables
    .local/bin/bashy
      Companion tool for help and templates for scripts and libraries

    .local/bin/bashy-logadm
    .local/bin/bashy-logs
      View and manage Bashy logs

    .config/bashy/install.sh
      Install or uninstall Bashy hook in ~/.bashrc
### Extras for demostration and inspiration
    .local/bin/color.bash
      Functions for terminal colors. Not mandatory but recommended
      Automatically used by for error prompts etc when exist

    .local/bin/color-cubes
    .config/color/color-names
      Demo scripts providing useful information on terminal colors.
      Enable 256 colors in your terminal to see all color patterns.

    .local/bin/array.bash
      Functions for array manipulation

    .local/bin/input.bash
      Functions to prompt user for input

    .local/bin/bunique.bash
      Functions for temporary files with automatic cleanup

    .local/bin/csv.bash
      Functions for comma-separated data.

    .local/bin/mutex.bash
      Functions for mutual exclusion

    .local/bin/ppcsv
      'pritty print' command to demonstrate csv.bash.

    .local/bin/search
    .config/search/defaults.setopt
      Search'n'replace tool with extensive set of command line options.
      Modify default options to your needs.

    .local/bin/viconfig
      Demonstrates command completion to help editing files under ~/config
## Dependencies and requirements
Should work with Bash 4.3 or higher.
Path ~/.local/bin must be in $PATH.
## Author
https://github.com/jounihenrikki/bashy/
[Jouni Henrikki Vääriskoski](mailto:?to=jouni.vaariskoski@gmail.com&subject=Bashy&body=Hello%20Jouni,)
Work is under GNU General Public License [GPLv3](https://www.gnu.org/licenses/gpl-3.0.html)
