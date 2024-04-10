# 1. Study Linux Commands

| Name        | Hrishikesh Mahajan   |
| ----------- | -------------------- |
| PRN         | 22110292             |
| Roll Number | 321041               |
| Department  | Computer Engineering |
| Class       | Third Year           |
| Division    | A                    |
| Batch       | A2                   |

## Aim

The aim of assigning Linux commands for Cloud &amp; DevOps is to help students and professionals
become familiar with the essential commands required for managing cloud-based infrastructure
and deploying and managing applications in a DevOps environment.

## Theory

Linux commands are a set of instructions used to perform specific tasks on a Linux operating system. The commands are entered into the command-line interface (CLI) of the terminal or console, which is a text-based interface for interacting with the operating system.

Linux commands are often designed to be simple and straightforward, and they typically follow a standard syntax. Most commands consist of a command name followed by options and arguments.

The command name is the name of the command that you want to execute. Options modify the behavior of the command, and arguments provide additional information to the command.

### What is shell?

A **shell** is a special system program that provides an interface for the user to use operating system services through a CLI (Command Line Interface). The shell accepts **human-readable commands** from users and converts them into something which **the kernel can understand**. It is a command language interpreter that executes commands read from input devices such as keyboards or from files. The shell gets started when the user logs in or starts the terminal.

The shell can be accessed by users using a terminal emulator application in GUI (Graphical User Interface) or TTY (Text-based Terminal Interface) environments. Some popular shells include Bash (Bourne-Again SHell), Zsh, Fish, and Tcsh.

A special program called Terminal in Linux/macOS, or Command Prompt in Windows OS is provided to type in the human-readable commands such as `cat`, `ls`, etc.

## Linux Commands

1. `touch`   create new file
2. `ls` list contents of directory

    ```bash
    $ touch new.txt

    $ ls
    new.txt
    ```

3. `pwd` print working directory

    ```bash
    $ pwd
    /home/ubuntu/College/CC
    ```

4. `mkdir` make directory
5. `cd` change directory

    ```bash
    $ mkdir viit

    $ ls
    new.txt viit

    $ cd viit

    $ pwd
    /home/ubuntu/college/CC/viit
    ```

6. `echo` print message to shell

    ```bash
    $ echo "Hello World"
    Hello World
    ```

7. `cmd > file.txt` pass output of cmd in new created file.txt
8. `cmd >> file.txt` append output of cmd in file.txt
9. `cat` print contents of a file

    ```bash
    $ echo "Hello World" > file.txt

    $ ls
    file.txt

    $ cat file.txt
    Hello World
    ```

10. `cp` copy file/directory
11. `mv` move file/directory or rename
12. `rm` remove file/directory

    ```bash
    $ cp file.txt copied_file.txt

    $ ls
    copied_file.txt file.txt

    $ mv file.txt renamed.txt

    $ ls
    copied_file.txt renamed.txt

    $ rm renamed.txt

    $ ls
    copied_file.txt
    ```

13. `$var` return value of var
14. `read` read input from user

    ```bash
    $ read var
    1234

    $ echo $var is my input
    1234 is my input
    ```

15. `man` see manual of a command

    ```bash
    $ man ls

    NAME
          ls - list directory contents

    SYNOPSIS
          ls [OPTION]... [FILE]...

    DESCRIPTION
          List  information  about the FILEs (the current directory by default).  Sort entries
          alphabetically if none of -cftuvSUX nor --sort is specified.

          Mandatory arguments to long options are mandatory for short options too.

          -a, --all
    ```

16. `file` checks files type

    ```bash
    $ file copied_file.txt
    copied_file.txt: Unicode text, UTF-8 text
    ```

17. `zip` creates a zip archive
18. `unzip` extracts zip archive

    ```bash
    $ cd ..

    $ zip viit.zip viit/*

    $ ls
    new.txt viit.zip viit

    $ unzip viit.zip
    ```

19. `tar` Archives files without compression in a TAR format
20. `grep` searches string within a file and returns lines containing string

    ```bash
    $ echo this that >> new.file

    $ echo his hat >> new.file

    $ echo tis that >> new.file

    $ cat new.file
    this that
    his hat
    tis tat

    $ grep hat new.file
    this that
    his hat
    ```

21. `sed` edits strings in a file

    ```bash
    # we replace mango with apple
    $ echo "I like mango" | sed 's/mango/apple/g'
    I like apple
    ```

22. `head` prints first n (default 10) lines in a file

    ```bash
    # first 10 lines of this README.md file
    $ head README.md
    # 1. Study Linux Commands

    ## What is shell?

    A **shell** is a special user program that provides an interface for the user to use operating system services. Shell accepts **human-readable commands** from users and converts them into something which **the kernel can understand**. It is a command language interpreter that executes commands read from input devices such as keyboards or from files. The shell gets started when the user logs in or starts the terminal.

    Shell can be accessed by users using a command line interface. A special program called Terminal in Linux/macOS, or Command Prompt in Windows OS is provided to type in the human-readable commands such as “cat”, “ls” etc

    ## Linux Commands
    ```

23. `tail` prints last n (default 10) lines in a file

    ```bash
    $ tail README.md
    # last 10 lines of this file
        2 root      20   0       0      0      0 S   0.0   0.0   0:00.01 kthreadd
        3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp
        4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_par+

24. `sort` reorders files content

    ```bash
    $ cat new.txt
    abc abc
    this that
    his this
    this is my this

    # sorts contents of new.txt alphabetically
    $ sort new.txt
    abc abc
    his this
    this is my this
    this that
    ```

25. `locate` locates file in system and prints all paths

    ```bash
    # locate all the occurrences of .bashrc
    $ locate .bashrc
    /etc/bash.bashrc
    /home/ubuntu/.bashrc
    /usr/share/base-files/dot.bashrc
    /usr/share/doc/adduser/examples/adduser.local.conf.examples/bash.bashrc
    ```

26. `find` outputs a file or folders location, prints all the matching patterns

    ```bash
    # print all path of file matching with pattern '*.html'
    $ find ~/Codes/web/ -name '*.html'
    /home/ubuntu/Codes/web/test-site/index.html
    /home/ubuntu/Codes/web/portfolio/index.html
    /home/ubuntu/Codes/web/website/index.html
    ```

27. `chmod` change file permission

    ```bash
    $ cd viit

    $ ls -l
    .rw-r--r-- ubuntu ubuntu 0 B Fri Jan 19 11:22:32 2024 in_viit_after_touch.txt
    .rw-r--r-- ubuntu ubuntu 0 B Fri Apr  5 12:45:48 2024 script.sh

    $ chmod 744 script.sh
    .rw-r--r-- ubuntu ubuntu 0 B Fri Jan 19 11:22:32 2024 in_viit_after_touch.txt
    .rwxr--r-- ubuntu ubuntu 0 B Fri Apr  5 12:45:48 2024 script.sh
    # script.sh has permissions changed from rw- to rwx for this user
    ```

28. `ps` show running processes

    ```bash
    $ ps
        PID TTY          TIME CMD
      12655 pts/7    00:00:00 bash
      13551 pts/7    00:00:00 ps

    # running top in background
    $ top &

    $ ps
        PID TTY          TIME CMD
      12655 pts/7    00:00:00 bash
      13596 pts/7    00:00:00 top
      13602 pts/7    00:00:00 ps
    ```

29. `top` Monitor system processes in real-time.

    ```bash
    $ top

    %Cpu(s): 1.9 us, 0.4 sy, 0.0 ni, 97.7 id,0.0 wa, 0.0 hi, 0.0 si,0.0 st
    MiB Mem : 15736.5 total,  8088.7 free, 4177.5 used,  4596.8 buff/cache
    MiB Swap:   977.0 total,   977.0 free,    0.0 used, 11559.0 avail Mem

      PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
    1701 ubuntu      20   0  949768 140452  73644 S   5.0   0.9   0:23.12 kitty
    11049 ubuntu      20   0   50908  46380   9248 S   4.3   0.3   0:34.36 nvim
    1284 ubuntu      20   0 2171304 191944 126208 S   3.0   1.2   3:01.30 kwin_wa+
    2345 ubuntu      20   0   18.9g 330912  97800 S   3.0   2.1   4:12.58 WebExte+
    2165 ubuntu      20   0 3949992 529892 224328 S   2.0   3.3  16:34.84 firefox+
    3157 ubuntu      20   0   45724  40928   3088 S   1.3   0.3   0:09.50 tmux: s+
      41 root      20   0       0      0      0 S   0.3   0.0   0:00.08 ksoftir+
    1920 ubuntu      20   0  473556  18452  12012 S   0.3   0.1   0:00.61 xdg-des+
    8937 root       0 -20       0      0      0 I   0.3   0.0   0:02.74 kworker+
    11039 ubuntu      20   0   13764   8140   6776 S   0.3   0.1   0:01.48 nvim
    12445 root      20   0       0      0      0 I   0.3   0.0   0:00.21 kworker+
    12611 root      20   0       0      0      0 I   0.3   0.0   0:01.75 kworker+
    13699 ubuntu      20   0   11628   5096   3196 R   0.3   0.0   0:00.02 top
        1 root      20   0  168188  12924   9268 S   0.0   0.1   0:00.89 systemd
        2 root      20   0       0      0      0 S   0.0   0.0   0:00.01 kthreadd
        3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp
        4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_par+
    ```

30. `uname` Print system information

    ```bash
    $ uname -a
    Linux deblinu 6.1.0-18-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.1.76-1 (2024-02-01) x86_64 GNU/Linux
    ```
