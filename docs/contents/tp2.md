---
title: Lab 2 - File system and permissions
---

# Lab 2 - File system and permissions

!!! info "Instructions"

    - We recall that in all exercises the `$` at the beginning of the command represents the prompt, it is not to be entered when you write a command line.
    - For each new command, do not hesitate to consult its manual page with the `man` command, or to use the `--help` option (if it is available) to know what it does.


## File system

!!! tip "Linux file system"

    Linux file system is a *tree* or *hierarchy* of files and directories. The root directory is `/` and all other directories are subdirectories of it. Directories are separated by `/` and files are file names.

    When you open a shell (i.e. open a terminal), it is *in* a directory. This directory is called your *current directory* or *working directory*.
    
    A basic Linux system has tens of thousands of system directories and files. Most of these directories and files are hidden and are not visible by default. These hidden files and directories are used by the operating system to store configuration information and other system information.

    Root subdirectories are typically reserved for system files. The `/home` and `/tmp` directories are used to store temporary files and personal files.

    Unless you are a system administrator, you do not need to worry about most system files and directories. However, it is important to understand how directories and files are organized so that you can navigate the file system and find the files you need.

    The following table describes the contents of the main Linux file system directories.

    | Directory | Description |
    ------------ | -------------
    | `/bin` | Contains the programs essential to the operation of the system. |
    | `/boot` | Contains the files needed to boot the system. |
    | `/dev` | Contains the files representing the devices. |
    | `/etc` | Contains the system configuration files. |
    | `/home` | Contains the personal directories of the users. |
    | `/lib` | Contains shared libraries and kernel modules. |
    | `/media` | Contains the mount points of removable devices. |
    | `/mnt` | Contains the mount points of temporary file systems. |
    | `/opt` | Contains additional software. |
    | `/proc` | Contains information about processes and the system. |
    | `/root` | Administrator's home directory. |
    | `/run` | Contains application runtime files. |
    | `/sbin` | Contains the programs essential to the operation of the system. |
    | `/srv` | Contains the data of the services provided by the system. |
    | `/sys` | Contains information about devices. |
    | `/tmp` | Contains temporary files. |
    | `/usr` | Contains programs, libraries and configuration files. |
    | `/var` | Contains variable files such as logs, mails, databases, etc. |
    | `/lost+found` | Contains files recovered during a system crash. |

---

### Exercise 1 : `id` and `/etc/passwd`

1. Type the following commands in a terminal and note the results:
   ```bash
   $ id
   ```
2. Then type the same command, but this time with the argument `root`, note the results.
   ```bash
   $ id root
   ```
3. Then display the contents of the file `/etc/passwd` with the `cat` command.
4. Search for the lines where your username and the username `root` appear. What are the differences?
5. Can you deduce what the `/etc/passwd` file is used for?

## Normal files permissions

!!! tip "File protection"

    A Linux system allows many users to access files and directories. To protect files and directories, Linux uses a system of permissions. Permissions are access rights to files and directories. Permissions are associated with users and groups. Users are *people* who have an account on the system.

    For normal files, permissions are associated with three categories of users: the owner of the file (usually the one who created the file), the owner group of the file and other users.

    The permission categories for a file are as follows:

      - **read** `r`: allows you to read the contents of the file.
      - **write** `w`: allows you to modify the contents of the file.
      - **execute** `x`: allows you to execute the file (if it is a program or a script).

    The `-l` option of the `ls` command displays the meta-data associated with a file, its name, its size, its owner, its group, ... and in particular its permissions, for example:

    ```bash
    $ ls -l fichier
    -rw-r--r-- 1 user group 0 2019-09-09 10:00 fichier
    ```
    The string `-rw-r--r--` represents the permissions associated with the file. The first character designates the type of file, the next three represent the permissions of the owner, the next three represent the permissions of the owner group and the last three represent the permissions of other users. Permissions are represented by the characters `r`, `w` and `x` for read, write and execute permissions respectively. If the permission is not granted, the character `-` is used instead.

    Permissions can be represented by **numbers (octal representation)** or **letters (symbolic representation)**.

    The following table gives the correspondence between the two representations:

    | Numbers | Letters | Description |
    | ------- | ------- | ----------- |
    | 0 | `---` | No permission |
    | 1 | `--x` | Execute |
    | 2 | `-w-` | Write |
    | 3 | `-wx` | Write and execute |
    | 4 | `r--` | Read |
    | 5 | `r-x` | Read and execute |
    | 6 | `rw-` | Read and write |
    | 7 | `rwx` | Read, write and execute |

    In our example, the permissions `-rw-r--r--` can be represented in the following ways:

    | | User | Group | Other |
    |-|----------- | ------ | ------ |
    | symbolic | `rw-` | `r--` | `r--` |
    | binary | 110 | 100 | 100 |
    | octal | 6 | 4 | 4 |
---

### Exercise 2 : File permissions

1. Create an empty directory and an empty file (these two must be at the same level). Use the `ls` command and the `-l` and `-d` options on each of these two new files to determine the permissions you (respectively your group and others) have on these files. How do you recognize a directory?
2. The following lines give the answer of the `ls -ld` command on a certain directory (for the needs of the Exercise we have reported only the first and the last field of the result of `ls -ld`).
    ```bash
    drwxr-xr-x a
    dr-xr--r-- b
    -rw-r--r-- c.txt
    --w--w-r-- d.c
    -rwxr-xr-x op
    ```
    Among these files, which are the directories?
3. For each of the files above, give the permissions associated with each of the users (owner, owner group and other users) using the symbolic representation and the octal representation.
4. Give the symbolic representation and the octal representation of the permissions associated with the file `/etc/passwd`, the command `ls` and your home directory.

### Exercise 3 : Modify permissions `chmod`

1. Test the following commands in a terminal and try to understand how the `chmod` command works (with the symbolic representation).
    ```bash
    $ touch f; ls -l f
    $ chmod a= f; ls -l f
    $ chmod o+rw f; ls -l f
    $ chmod u=o f; ls -l f
    $ chmod o-wx f; ls -l f
    $ chmod g+u f; ls -l f
    $ chmod a+x,g-w f; ls -l f
    ```
2. Test the command `chmod 644 f; ls -l f`. What does this command do?
3. With the two modes of use of `chmod` (octal and symbolic), modify the permissions of the file `f` as follows:
    - execution for all, read and write only for the owner.
    - read and execute for all, no one can write.
    - all permissions for all, no writing for others.
    - read and write for the owner, execution for the group and none for others.

### Exercise 4 : Normal files permissions

1. In a directory of your choice, create two files `f` and `g`. Then enter (for example with a text editor) text in these files.
2. For you (owner), remove the read permission in the file `f` and the write permission in the file `g`.
3. Then test the following commands, then note the results:
    ```bash
    $ cat f
    $ cat g
    ```
4. Try to modify `g` with a text editor. What happens?
5. Test the commands:
    ```bash
    $ cp f h
    $ cp g h
    ```
    Then observe the content of the file `h` as well as the permissions associated with this file.
6. The following command allows you to write the string `toto` at the end of the file `f` (we will see it in more detail in a future Lab session):
    ```bash
    $ echo "toto" >> f
    ```
    Test this command, then give yourself back the read permission on the file `f`. Finally display the content of the file `f` with the `cat` command.
7. Test the command:
    ```bash
    $ rm g
    ```
    **Type `n` to refuse**. Finally test the following command:
    ```bash
    $ rm -f g
    ```
    Did it succeed? What can you deduce from this?

## Directories permissions

!!! tip "What is a directory ?"

    A directory is a table of file names associated with an index number called *inode number* which allows to know the information (contained in the inode) concerning this file (size, permissions, timestamp, where to find the content of the file, ...).

    In a directory, permissions are not associated with files but with the directory itself. The permissions associated with a directory are:

      - **read** `r`: allows you to list the contents of the directory.
      - **write** `w`: allows you to modify the contents of the directory (create or delete files).
      - **execute** `x`: allows you to open the directory (with the `cd` command for example).
---

### Exercise 5 : Directories permissions

1. Create a directory `rep` and two normal files `a` and `b` inside this directory.
2. Remove all permissions on the directory `rep` and try the following commands:
    ```bash
    $ cd rep
    $ ls rep
    $ cat rep/a
    $ touch rep/c
    $ rm rep/a
    ```
3. Give only the *read* permission on the directory `rep` and try all the commands of question 2. Note the differences.
4. Same question but with only the *write* permission on `rep`. Note the differences.
5. This time with only the *execute* permission on `rep`. Test the following commands:
    ```bash
    $ cd rep
    $ ls rep
    $ echo "toto" >> rep/a
    $ cat rep/c
    $ ls -l rep/a
    $ touch rep/c
    $ rm rep/a
    ```
6. With the set of permissions `-wx` on `rep` for all users, try to:
      - create a file d in `rep`
      - rename the file b
      - remove all permissions associated with the file d
      - delete the file d
  
### Exercise 6 : `PATH` diretories

!!! warning "Caution"

    This kind of exercise is delicate and important. It must be treated with particular care and taking your time.

1. Open a new terminal and enter the following command:
    ```bash
    $ echo $PATH
    ```
    Observe the result, in your opinion what do the elements separated by `:` correspond to?
2. Create a `bin` directory in your home directory and enter the following commands:
    ```bash
    $ PATH=~/bin:$PATH
    $ echo $PATH
    ```
    What is the difference with the display with the result of question 1?
3. Using the `type` command, look for the absolute paths of the `cat` and `rm` programs and note them.
4. Copy `cat` to `~/bin` by renaming it `rm`.
5. Create a `fic` file, put some characters in it and create two copies `fic2` and `fic3` of `fic`.
6. Try to destroy `fic` with the `rm` command. What happened?
7. Enter the command `$ type rm`.
8. Run the command
    ```bash
    $ <path to rm> fic
    ```
    replacing `<path to rm>` with the absolute path to the `rm` command noted in question 3. What happened?
9. Remove the `x` permission on the `~/bin/rm` file and try to delete `fic2`.
10. Ask the shell to forget the saved (hashed) locations with the command `$ hash -r`, then enter the commands
    ```bash
    $ type rm
    $ rm fic2
    ```
11. Put back the `x` permission on `~/bin/rm` then enter the following commands (where `<path to rm>` denotes the absolute path noted in question 3):
    ```bash
    $ ~/bin/rm fic3
    $ cd ~/bin
    $ ./rm fic3
    $ <path to rm> rm
    $ rm fic3
    ```
12. Make a synthesis of this exercise by answering the following questions:
    -  What is contained in `PATH`?
    -  In which case is a command name searched in the `PATH` directories?
    -  If there are several corresponding programs in the `PATH` directories, which one is chosen?

## Sum up on permissions and default permissions

### Exercise 7 : Hands off!

!!! info "Instructions"

    This exercise has to be done on paper, hands off the keyboard!

For each of the following commands, say what permissions are needed for it to succeed (we assume that all directories and files exist, except those we want to create).

```bash
$ cat /usr/include/stdio.h
$ cd /usr/include/
$ ls /usr/include/
$ echo '/* fin */' >> /usr/include/stdio.h
$ rm /usr/include/stdio.h
$ touch /usr/include/ma_bib.h
$ chmod u+w /usr/include/stdio.h
$ /usr/bin/uname
```

### Exercise 8 : Default permissions and `umask` (optional)

!!! tip "What us `umask` ?"

    `umask` is a built-in command that allows you to define the default permissions of files and directories that you create. The value of the umask is an octal value that is *subtracted* from the default permissions. For example, if the umask is 022, the default permissions are 755 for directories and 644 for files.

---



1. In a terminal, type the command `umask` and note the result.
2. Create a directory `rep` and a file `f` at the same level as `rep`. Display the permissions associated with `rep` and `f` with the command `ls -ld rep f`. Convert these permissions to octal representation and note them. Finally, delete `rep` and `f`.
3. Change the value of the mask with the command
    ```bash
    $ umask 240
    ```
4. Change the value of the mask with the command
    ```bash
    $ umask 121
    ```
    then redo question 2.
5. Change the value of the mask with the command
    ```bash
    $ umask 666
    ```
    then redo question 2.
6. From all the previous questions, can you deduce how the value of the umask affects the permissions associated with the directories and files you create?
7. Give back the umask its initial value.