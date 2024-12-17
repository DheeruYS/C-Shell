### Printing file permissions as a string

https://stackoverflow.com/questions/26616038/how-do-i-print-file-permissions-as-a-string and https://stackoverflow.com/questions/10323060/printing-file-permissions-like-ls-l-using-stat2-in-c

### Getting all stat related to a process

https://pubs.opengroup.org/onlinepubs/007904975/functions/stat.html

### Check if a process is foreground or background

https://stackoverflow.com/questions/50620264/from-a-c-program-how-to-know-if-the-process-is-running-in-the-foreground-or-bac

### Trim a string and Remove white spaces

https://stackoverflow.com/questions/656542/trim-a-string-in-c
https://stackoverflow.com/questions/1726302/remove-spaces-from-a-string-in-c

### Piping

https://stackoverflow.com/questions/8389033/implementation-of-multiple-pipes-in-c

### Raw Mode and Non blocking Input

https://viewsourcecode.org/snaptoken/kilo/02.enteringRawMode.html
https://unix.stackexchange.com/questions/437409/problems-caused-by-stdin-set-to-non-blocking-mode

### Neonate 

https://stackoverflow.com/questions/11987495/what-do-the-numbers-in-proc-loadavg-mean-on-linux

### Chat GPT 

![](SS1.png)
![](SS2.png)
![](SS3.png)
![](SS4.png)
![](SS5.png)
![](SS6.png)

### Assumptions

No. of files matching in seek is less than 1000

At max 1000 background processes are running

No . of files in reveal is less than 1000

If there is no previous directory, - is just the home directory

Coloring only file/directory name in reveal

For foreground process, I print the details as soon as the process ends and then ask for the next prompt

When giving the system command, multiple & is not given. For any background process, there is only 1 &

For I/O Redirection, First command is given and then the input and output files in any order.

vi,emacs and similar editors will be disabled in background

The status of the background process with output redirection will be printed in the file instead of the terminal