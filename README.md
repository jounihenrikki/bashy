# bashy
Personal and portable Bash scripting environment with useful built-in features

https://www.urbandictionary.com/define.php?term=bashy

## Libraries
Scripts can source all required .bash libraries with single command together with main library bashy.bash. Neẇ libraries can be created using a template.

## Logging and output
Enable specific logs to start logging. See 'logadm --help' and 'logs --help'. Functions: lib.log, lib.log-usage, lib.outlog, lib.out, lib.set-verbosity.

## Error handling
Bashy uses best practice error handling options: 'set -o errexit -o errtrace -o pipefail -o nounset'. ERR pseudo signal is handled by lib.traceback() to provide backtrace. Functions: lib.error, lib.fatal.

## Long options
Library setopt.bash supports strongly typed long command line options and option arguments. Common options like --help are handled automatically.

## Command completion
Library complete.bash supports automatic command completion for command line options, option arguments and user-defined words. Script 'compreg' can rebuild source files with complete commands for login scripts.

## Debugging
Library setopt.bash supports generic --debug command line option. Debug layers are registered in library source files or script using a function.

## Housekeeping
Pseudo-signal EXIT is trapped to call function lib.cleanup() on exit. Script or library can register additional functions to be run by lib.cleanup(). Automatic cleanup is used for example by 'bunique' and 'mutex' libraries.


# Files
Main source file bashy.bash must be in PATH, and other .bash libraries in turn must be in same directory. For simplicity they are with the executables.  
Bash source files - bashy libraries - in `~/.local/bin`

    bashy.bash        main source file library
    skeleton.bash     library file template
    array.bash        functions related to Bash arrays
    bunique.bash      create temporary files with auto-cleanup
    color.bash        add color support for error messages etc.
    complete.bash     support for command line completion
    input.bash        functions for user interaction
    mutex.bash        functions for mutual exclusion based on lock files
    validate.bash     datatype validation functions

Executable files - in `~/.local/bin` - if moved, must be in PATH

    bashy-eval        supports testing libraries interactively
    bashy-help        prints help on Bashy libraries
    color-cubes       displays color palettes, demo for color.bash
    compreg           builds source files for command line completion
    logadm            log management and housekeeping
    logs              log browser
    search            text search and replace tool
    skeleton          creates skeleton 'bashy-compatible' script
    viconfig          helps in editing configuration files

Configuration files in `~/.config`

    .config/complete.d/*.bash
      Command complation source files built by compreg

    .config/color.bash/color-names
      Color data for color.bash functions

    .config/search/defaults.setopt
      Defaults command line options for search script

Login scripts. I you choose not to use these as I do, copy the content of 1complete.bash to your `~/.bashrc`

    .config/bashrc
      Login source file (source this from ~/.bashrc). I source this also for non-interactive shells (e.g. run by cron) by setting BASH_ENV.

    .config/bashrc.d/1complete.bash
      All .bash files in the directory are sourced by .config/bashrc. 1complete.bash runs compreg to rebuild source files in ~/.config/complete.d/ and sources them.

## Dependencies and requirements
Bash 4.3 or higher required. Path ~/.local/bin must be in search PATH.

## Author
Jouni Henrikki Vääriskoski (jounihenrikki)  
mailto:?to=jouni.vaariskoski@gmail.com&subject=Bash%20scripting&body=Hi%20Jouni,%20the%20Bash%20wizard,  
Project is under GNU General Public License (GPLv3), https://www.gnu.org/licenses/gpl-3.0.html  
Thanks to my employer Telia https://www.teliacompany.com/ for letting me publish this core package.  

## Other work built on bashy, possibly to be published later

  alarmdb       File-based alarm database with smart email notifications etc.
  cronguard     Runs commands in crontab in smart way (requires alarmdb)
  cronmaster    Manage crontab sections for multiple users via ssh.
  deployment    Maintains scripts in multiple locations via ssh.
  sqlplus       Helps with Oracle SqlPlus ad-hoc queries and integration
