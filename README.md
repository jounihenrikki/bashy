# bashy
Personal and portable Bash scripting environment


Name
  Bashy - personal and portable Bash scripting environment

Description
  Bash scripting environment with some useful built-in features:

  Logging and output
    Functions: lib.log, lib.log-usage, lib.outlog, lib.out, lib.set-verbosity
    Support scripts: logs, logadm
    Enable logs to start logging. See logadm --help

  Error handling
    Functions: lib.error, lib.fatal (all errors are also logged)
    Bashy uses best practice error handling options:
    'set -o errexit -o errtrace -o pipefail -o nounset'
    ERR pseudo signal is handled by lib.traceback() to provide backtrace.

  Long options
    Source 'setopt' library to support strongly typed long command line options
    and option arguments. Common options like --help are processed automatically.

  Command completion
    With 'complete' library, supports automatic command completion for command
    line options, arguments and user-defined keywords. Support script 'compreg'
    can be run to rebuild source files for login scripts.

  Debugging
    Source 'setopt' library to support --debug command line option.
    Debug domain and debug layers are (typically) set in library source file.
    Functions: lib.debug-register (function lib.debug is for ad-hoc debugging).

  Housekeeping
    Pseudo-signal EXIT is trapped to call function lib.cleanup() on exit.
    User can register additional functions to be run by lib.cleanup().
    Automatic clenaup is used by 'bunique' and 'mutex' libraries.

Files
  Main source file bashy.bash must be in PATH, and other .bash libraries must
  be in same directory, so for simplicity they are all in ~/.local/bin.

  Files in root install directory (user's HOME directory)
    README           This file
    LICENSE          GPLv3 License

  Bash source files (Bashy libraries) in ~/.local/bin
    bashy.bash        main source file library
    skeleton.bash     library file template

    array.bash        functions related to Bash arrays
    bunique.bash      create temporary files with auto-cleanup
    color.bash        add color support for error messages etc.
    complete.bash     support for command line completion
    input.bash        functions for user interaction
    mutex.bash        functions for mutual exclusion based on lock files
    validate.bash     datatype validation functions

  Executable files in ~/.local/bin (must be in PATH)
    bashy-eval        supports testing libraries interactively
    bashy-help        prints help on Bashy libraries
    color-cubes       displays color palettes, demo for color.bash
    compreg           builds source files for command line completion
    logadm            log management
    logs              log browser
    search            text search and replace tool
    skeleton          creates skeleton 'bashy-compatible' script
    viconfig          helps in editing configuration files

  Configuration files in ~/.config
    bashrc
      login source file (source from ~/.bashrc)

    bashrc.d/1complete.bash
      runs compreg to rebuild source files in ~/.config/complete.d/ and sources
      them. sourced by ~/.config/bashrc

    complete.d/*.bash
      command complation source files built by compreg

    color.bash/color-names
      color data for color.bash functions

    search/defaults.setopt
      defaults command line options for search script

Dependencies and requirements
  Bash 4.3 or higher required.
  Path ~/.local/bin must be in search PATH.

Housekeeping
  Log file housekeeping is handled by 'logadm --housekeeping'. If you have
  enabled logs (by script or library name), schedule command in cron or run it
  every now and then.

Copyright
  2022 Jouni Henrikki Vääriskoski
  Project is under GNU General Public License (GPLv3), https://www.gnu.org/licenses/gpl-3.0.html

Author
  Jouni Henrikki Vääriskoski
  mailto:?to=jouni.vaariskoski@gmail.com&subject=Bash%20scripting&body=Hi%20Jouni,%20the%20Bash%20wizard,

Other work built on Bashy, possibly to be distributed later.
  alarmdb       File-based alarm database with smart email notifications etc.
  cronguard     Runs commands in crontab in smart way (requires alarmdb)
  cronmaster    Manage crontab sections for multiple users via ssh.
  deployment    Maintains scripts in multiple locations via ssh.
  sqlplus       Helps with Oracle SqlPlus ad-hoc queries and integration
