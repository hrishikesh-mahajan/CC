# 2. Shell Scripting

| Name        | Hrishikesh Mahajan   |
| ----------- | -------------------- |
| PRN         | 22110292             |
| Roll Number | 321041               |
| Department  | Computer Engineering |
| Class       | Third Year           |
| Division    | A                    |
| Batch       | A2                   |

## Aim

The aim of an assignment that requires the use of Shell Scripting is to help students develop practical skills in automating tasks on a Linux system using scripting languages. Shell scripting is an important skill for any IT professional working in Linux environments, as it can help to simplify and automate complex tasks, reduce errors, and save time and effort. Shell scripts can be used for a wide range of purposes, such as system administration, file management, network configuration, and more.

## Theory

### What is a shell?

**A shell** is a special user program that provides an interface for the user to use operating system services. Shell accepts **human-readable commands** from users and converts them into something that **the kernel can understand**. It is a command language interpreter that executes commands read from input devices such as keyboards or from files. The shell gets started when the user logs in or starts the terminal.

![Shells|400x400](https://cdn.mindmajix.com/blog/images/linux-0203-1919.png)

Shell can be accessed by users using a command line interface. A special program called Terminal in Linux/macOS, or Command Prompt in Windows OS is provided to type in human-readable commands such as `cat`, `ls`, etc

### Different types of shells

| Shell                        | Complete path-name | Prompt for root user | Prompt for non root user |
| ---------------------------- | ------------------ | -------------------- | ------------------------ |
| GNU Bourne-Again shell(bash) | /bin/bash          | bash-VersionNumber#  | bash-VersionNumber$      |
| C shell (csh)                | /bin/csh           | #                    | %                        |
| Korn shell (ksh)             | /bin/ksh           | #                    | $                        |
| Z shell (zsh)                | /bin/zsh           | "hostname"#          | "hostname"%              |

## Problem statements for shell scripting

### 2a) Write a shell script to check whether the user is the root user or not (HINT: study "id" command in Linux)

`id` command outputs information about the current user.

Normal User:

```bash
$ id
uid=1000(ubuntu)gid=1000(ubuntu)groups=1000(ubuntu),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),44(video),46(plugdev),100(users),106(netdev),112(bluetooth),114(lpadmin),118(scanner)
```

Root User:

```bash
# id
uid=0(root) gid=0(root) groups=0(root)
```

With both of these outputs, we can grep string root from these outputs. If `grep` doesn't return anything it will be treated as false in the if statement and we can say that the user is not the root user, otherwise the user is a root user.
The output of the above script is as follows

Normal User:

```bash
$ ./check_user.sh
This is not root user
```

Root User:

```bash
# ./check_user.sh
This is root user
```

### 2b) Write a shell script to install any particular software (ex: java or Python)

One of the most important features of Linux is the availability of software via package managers. Package managers are the command line tools that help install applications, and software via a single command. It's a more preferred way to install an application than clicking in a GUI window multiple times.
Based on different Linux distributions, different package managers are used. All these package managers have different versions of packages available

Ex. if you are using Debian Debian-based distro you are using an `apt` package manager which is known to ship only stable packages. It means you will get stable, bug-free software but you may have to wait to get the latest and greatest features. For Arch-based distros, you use a package manager named Pacman. It is a bleeding edge package manager which means you get the latest features as soon as they are released by developers, on the risk of packages breaking your system and encountering bugs. Fedora, you come across a package manager called `dnf` which is false under the bleeding edge side of package managers but not as fast as Pacman so you get the best of both worlds.

While writing a script to install a package we first must know on which distro we are so we can choose our package manager.
The information about our distro is stored in the `/etc/os-release` file.

```bash
$ cat /etc/os-release
PRETTY_NAME="Debian GNU/Linux 12 (bookworm)"
NAME="Debian GNU/Linux"
VERSION_ID="12"
VERSION="12 (bookworm)"
VERSION_CODENAME=bookworm
ID=debian
HOME_URL="https://www.debian.org/"
SUPPORT_URL="https://www.debian.org/support"
BUG_REPORT_URL="https://bugs.debian.org/"
```

Here, we can see the attribute ID which will give us the name of the distro, we will try to get the distro name from this file.

```bash
# cat install.sh
#!/bin/bash
if [[ $(grep "debian" /etc/os-release) ]]; then
    echo "debian based system recognised"
    sudo apt update
    sudo apt upgrade
    sudo apt install python3

elif [[ $(grep "arch" /etc/os-release) ]]; then
    echo "arch based system recognised"
    sudo pacman -Syu
    sudo pacman -S python-pip

elif [[ $(grep "fedora" /etc/os-release) ]]; then
    echo "fedora based system recognised"
    sudo dnf upgrade
    sudo dnf install python
else
    echo "unknown system recognised"
fi

```

This universal script installs Python on the listed 3 distros (and their sub-distros).

### 2c) Write a shell script to check the disk usage of the system and if disk usage is more than 90% it should send an email to the system admin. This script should run every day at 8:00 AM

the `du` command returns disk usage of the specified directory

```bash
# gives disk used by user directory
$ du -sh ~
20G /home/ubuntu
```

There is also `df` command which gives the amount of space available on the file system.

```bash
$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
udev             8023760        0   8023760   0% /dev
tmpfs            1611424     1692   1609732   1% /run
/dev/nvme0n1p5 300278136 38525400 246426376  14% /
tmpfs            8057116     3684   8053432   1% /dev/shm
tmpfs               5120        8      5112   1% /run/lock
/dev/nvme0n1p1     98304    50418     47886  52% /boot/efi
tmpfs            1611420       76   1611344   1% /run/user/1000

```

Our system is on the `/dev/nvme0n1p5` file system, there we can see Use% being 14%, we can extract this percentage value from here. For that, we will use grep and sed.

To send mail, we will use the mail command:

```bash
echo "message you want to send" | mail -s "subject of mail" "to_user@xyz.com"
```

So the script becomes the following:

```bash
#!/bin/bash
percentage_usage=$(df | grep "p5" | grep "[0-9]*%" --only-matching)
percentage_usage=$(echo "$percentage_usage" | sed s'/.$//')
echo "$percentage_usage"

if [[ $percentage_usage -gt 90 ]]; then
    # send mail
    message="Disk usage on the system has exceeded 90% threshold. Current usage is $percentage_usage %"
    echo "$message" | mail -s "Disk usage alert" admin@email.com
fi
```

To run this script every day at 8 AM add the following lines to the crontab file.

```bash
0 8 * * * /path/to/check_usage.sh
```

### 2d) Write a shell script to take MySQL database server backup. This script should run weekly every Sunday at 11:00 PM

```bash
#!/bin/bash

# MySQL database credentials
DB_USER="your_username"
DB_PASS="your_password"
DB_NAME="your_database_name"

# Backup directory
BACKUP_DIR="/path/to/backup/directory"

# Date format for backup file
DATE=$(date +"%Y%m%d_%H%M%S")

# Dump the MySQL database
mysqldump -u "${DB_USER}" -p"${DB_PASS}" "${DB_NAME}" > "${BACKUP_DIR}/${DB_NAME}_${DATE}.sql"

# Check if the backup was successful
if [ $? -eq 0 ]; then
    echo "MySQL database backup completed successfully."
else
    echo "Error: MySQL database backup failed."
fi
```

To schedule this script to run weekly on Sundays at 11:00 PM, you can set up a cron job. Add the following line to your crontab.

```bash
0 23 * * 0 /path/to/mysql_backup.sh
```

## Conclusion

Shell scripting assignments successfully, students can gain valuable experience that will prepare them for real-world IT environments, where automation and efficiency are essential. Helps develop practical skills in automating tasks on a Linux system using scripting languages.
