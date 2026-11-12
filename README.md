# Bashy
Framework for Bash scripting, written in Bash.

Bashy is a modular, lightweight scripting framework designed to bring high-level application structure, robust error handling, and user-friendly CLI features natively to Bash 4.4+ without introducing external runtime dependencies.

---

## Components and features
### 1. Core Framework (`bashy.zip`)
The foundation of the environment establishes key paradigms for robust, production-grade scripting:
* **`bashy.bash`**, **`setopt.bash`**, **`validate.bash`**, **`input.bash`**: These modules address traditional Bash shortcomings by providing strongly typed option parsing, robust argument validation, and structured user input handling. By mimicking standard library behaviors found in higher-level languages (like Python or Go), they prevent scripts from failing silently due to malformed inputs.
* **Exit and Error Traps**: The framework leverages Bash's `ERR` pseudo-signal for automated backtracing/debugging and traps the `EXIT` pseudo-signal for registered housekeeping and cleanup routines. This ensures that system resources are cleaned up properly even if a script terminates unexpectedly.
* **Configuration Portability**: Adheres to modern standards (akin to the XDG Base Directory Specification) by supporting multiple configuration fallback paths. Configurations adapt cleanly across diverse environments without hardcoding absolute system paths.

---

### 2. Command Line Completion (`bashy-complete.zip`)
* **`complete.bash`**: Introduces dynamic command-line completion for options, enumerated arguments, and positional parameters without requiring external configuration files outside the script itself. For embedded devices or minimal appliances like home routers, having self-contained completion logic embedded directly in the script structure keeps overhead minimal.

---

### 3. Logging and Housekeeping (`bashy-log.zip`)
* **`log.bash`**, **`bashy-logadm`**, **`bashy-logs`**: Introduces a lightweight log database and management utilities. Capturing script invocations by default provides crucial audit trails and diagnostics on headless or isolated appliances where interactive debugging can be difficult.

---

### 4. Terminal Presentation (`bashy-color.bash`)
* **`color.bash`**: Provides clean ANSI color abstraction that automatically hooks into error messaging (`bashy.error()`) and command help output when detected. It improves CLI readability while remaining lightweight.

---

### 5. Additional stuff (`bashy-util.bash`)
* **`array.bash`**: High-level array manipulations.
* **`csv.bash`** / **`ppcsv`**: Native CSV parsing and pretty-printing.
* **`mutex.bash`**: File-based mutual exclusion and concurrency control.
* **`bunique.bash`**: Wrapper for mktemp(1). With EXIT hook to automatically delete temporary files on exit.
* *Note:* The `mutex.bash` library is particularly valuable in resource-constrained environments (such as background cron jobs) to prevent race conditions and duplicate process execution.

---

## Installation
Bashy libraries are installed under user's home by default.\
1. First clone the repo or copy the zip files to any folder
2. Use the install script or source .config/bashyrc' from ~/.bashrc
3. Source bashyrc manually to current shell (or relogin) and you're ready to go
```console
    $ git clone https://github.com/jounihenrikki/bashy.git
    $ unzip bashy.zip
    $ unzip bashy-complete.zip # for command completion (optional but highly recommended)
    $ unzip bashy-color.zip # for ANSI color support (optional)
    $ unzip bashy-log.zip # for logging (optional)
    $ ~/.config/bashy/install.sh # install hook to .bashrc
    $ source ~/.config/bashyrc # or relogin
```
## Uninstallation
1. Uninstall optional packages (all except 'bashy')
2. Remove the hook manually from \~/.bashyrc or by using the script
3. Uninstall 'bashy' base package
4. Delete logs if you had log.bash installed
```console
    $ bashy uninstall bashy-<package> # do for each package (use command completion!)
    $ ~/.config/bashy/install.sh -u
    $ bashy uninstall bashy
    $ rm -rf ~/.local/state/bashy-logs
```
## To propagate set of packages to another user or appliance
Pack a collection of packages. Copy zip to remote host or user, unzip and install
```console
    $ bashy package bashy <package> ...
    $ scp bundle.zip <login>:
    $ ssh <login> unzip bundle.zip
    $ ssh <login> .config/bashy/install.sh
```
## To get help
```console
    $ bashy help [<library>.bash] # Get help on library in ~/.local/bin. or bashy.bash by default.
    $ bashy sekelton-with-comments [<filename>] # Create script skeleton with comments in ~/.local/bin
    $ <command> --help # All scripts document themselves, help option is built-in.
    $ bashyrc.help # Help on functions for interactive use
```
---

## Summary of Strengths for Appliance Deployment (as analyzed by AI)

1. **Zero External Language Dependencies**: Written entirely in native Bash 4.4+, avoiding the overhead of installing Python, Perl, Node.js, or compiled runtimes on space-constrained Flash storage.
2. **Seamless Packaging & Propagation**: The modular `bashy package` utility allows developers to bundle scripts and libraries into tiny zip archives, enabling rapid deployment via standard network tools (`scp`/`ssh`).
3. **Defensive Scripting Design**: Built-in data validation, automatic exception trapping, and systematic cleanup traps reduce the likelihood of leaving an unattended edge device in an inconsistent state.

---

## Author
https://github.com/jounihenrikki/bashy/\
Work is under GNU General Public License [GPLv3](https://www.gnu.org/licenses/gpl-3.0.html)\
Introduction part of README is mostly written by AI.
