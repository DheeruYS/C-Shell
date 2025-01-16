# Project : C Shell

## Project Background

This project was developed as a Mini-Project as part of the _CS3.301 Operating Systems and Networks at IIIT-Hyderabad_.

Developed a custom Linux shell in C with features including command execution, I/O redirection, piping,
process management (foreground and background), signal handling (including keyboard inputs), networking capabilities,
and support for blocking and non-blocking inputs.

## Project Description
Link to course website :  https://karthikv1392.github.io/cs3301_osn/mini-projects/mp1

## Overview
This project implements a custom shell in C that simulates a command-line interface similar to Unix-like environments. The shell provides various functionalities, including command execution, directory navigation, file listing, and command logging, all while maintaining a user-friendly prompt.


## Features 
### 1. **Dynamic Shell Prompt**
The shell displays a prompt in the format `<Username@SystemName:~>` where:
- `Username` is the current user's name.
- `SystemName` is the name of the system.
- The prompt reflects the current working directory, using `~` for the home directory.

### 2. **Command Input Handling**
- Supports commands separated by `;` or `&`.
- Handles random spaces and tabs in input.
- Commands can be executed sequentially or in the background.

### 3. **Directory Navigation (`hop` Command)**
- Changes the current directory and prints the full path.
- Supports both absolute and relative paths.
- Special flags like `.`, `..`, `~`, and `-` are implemented for ease of navigation.

### 4. **File Listing (`reveal` Command)**
- Lists files and directories in lexicographic order.
- Supports flags `-a` (show hidden files) and `-l` (detailed information).
- Color coding differentiates between file types: 
  - Green for executables
  - White for files
  - Blue for directories

### 5. **Command Logging (`log` Command)**
- Keeps track of the last 15 unique commands executed across sessions.
- Supports commands to purge logs and execute commands from history by index.
- Does not log the `log` command itself.

### 6. **System Command Execution**
- Execute system commands (e.g., `emacs`, `gedit`) in foreground or background.
- **Foreground**: Waits for completion; prints execution time if over 2 seconds.
- **Background**: Commands with `&` run without waiting; displays PID and status upon completion.

### 7. **Process Information (`proclore` Command)**
- Displays info about a process or the shell:
  - PID, Status (R/R+/S/S+/Z), Group, Virtual Memory, Executable Path.

### 8. **File Searching (`seek` Command)**
- Searches for files/directories in a specified directory (or current).
- Returns matching paths; flags:
  - `-d`: Only directories.
  - `-f`: Only files.
  - `-e`: Print or change to single match.
- Format:  seek < flags >  < search > < target_directory >

### 9. **I/O Redirection**
- Supports `>`, `>>`, and `<` for output/input redirection:
  - `>`: Redirects output to a file (overwrites if exists).
  - `>>`: Appends output to a file.
  - `<`: Reads input from a file.
- Displays "No such input file found!" if the input file does not exist.
- Creates the output file with permissions 0644 if it does not exist.

### 10. **Pipes**
- Passes output from one command to the input of another using pipes (`|`).
- Supports multiple pipes; commands run sequentially from left to right.
- Displays "Invalid use of pipe" if improperly used (e.g., no command on either side).

### 11. **Redirection with Pipes**
- Combines I/O redirection and pipes, allowing both functionalities to work together.
- Supports any number of pipes but not multiple inputs/outputs from I/O redirection.

### 12. **Activities (`activities` Command)**
- Lists all currently running processes spawned by the shell in lexicographic order.
- Displays the following information for each process:
  - Command Name
  - PID
  - State (running or stopped)
- Format: [pid] : [command name] - [State]


### 13. **Signals (`ping` Command)**
- Sends a signal to a process using `ping <pid> <signal_number>`.
- Displays "No such process found" if the given PID does not exist.
- The signal number is taken modulo 32 to determine the corresponding signal.

#### Keyboard Signals:
- **Ctrl - C**: Sends SIGINT to interrupt the currently running foreground process.
- **Ctrl - D**: Logs out of the shell after terminating all processes.
- **Ctrl - Z**: Pushes the foreground process to the background, changing its state to stopped.

### 14. **Foreground and Background Management**
- **Foreground (`fg <pid>`)**: Brings a running or stopped background process to the foreground, taking control of the terminal. Displays "No such process found" if the PID does not exist.

- **Background (`bg <pid>`)**: Changes a stopped background process to running (in the background). Displays "No such process found" if the PID does not exist.

### 15. **Neonate (`neonate -n [time_arg]` Command)**
- Prints the Process-ID of the most recently created process every `[time_arg]` seconds.
- The output continues until the user presses the key 'x'.

### 16. **iMan (`iMan <command_name>` Command)**
- Fetches man pages from the internet using sockets from `http://man.he.net/`.
- Outputs the man page for the specified command to the terminal (stdout).
- HTML tags and header are removed while displaying the outptu.

## Usage Instructions
1. **Compiling the Shell**
   To compile the project, use:
   
    ```make``` 
2. **Running the Shell**
Execute the shell with :
 
    ```./a.out```
3. **Command Examples** 
Some command examples and execution can be find in the screenshots folder.

## Resources Used : 
1. https://stackoverflow.com/questions/26616038/how-do-i-print-file-permissions-as-a-string and https://stackoverflow.com/questions/10323060/printing-file-permissions-like-ls-l-using-stat2-in-c
2. https://pubs.opengroup.org/onlinepubs/007904975/functions/stat.html
3. https://stackoverflow.com/questions/50620264/from-a-c-program-how-to-know-if-the-process-is-running-in-the-foreground-or-bac
4. https://stackoverflow.com/questions/656542/trim-a-string-in-c
5. https://stackoverflow.com/questions/1726302/remove-spaces-from-a-string-in-c
6. https://stackoverflow.com/questions/8389033/implementation-of-multiple-pipes-in-c
7. https://viewsourcecode.org/snaptoken/kilo/02.enteringRawMode.html
8. https://unix.stackexchange.com/questions/437409/problems-caused-by-stdin-set-to-non-blocking-mode
9. https://stackoverflow.com/questions/11987495/what-do-the-numbers-in-proc-loadavg-mean-on-linux
## 