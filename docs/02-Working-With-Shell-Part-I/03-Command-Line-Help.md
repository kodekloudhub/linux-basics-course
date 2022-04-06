# Using command line to get help

- Take me to the [Video Tutorial](https://kodekloud.com/topic/command-line-help-3/)

In this section we will learn how to use **`help`** command to get help in command line
- If you are new to using `linux` or `bash shell`  or if you are not sure which command does what, there are few commands in bash that can help get started. 
- Lets take a look of those

First command is **`whatis`** , this command will displays a one line description of a command does. 

**`Syntax: whatis <command>`**

```
$ whatis date
```

Most of the commands internal or external come bundled with **`man pages`** which provides information about the command in detail (with examples, usecases and with command options)

**`Syntax: man <command>`**

```
$ man date
```

Several commands will provide **`-h`** or **`--help`** to provide users with the options and usecases available in a command

```
$ date -h
$ date --help
```

To search through the man page names and descriptions for instances of the keyword use **`apropos`**. This is useful if you want to look for all commands within the system that contains the specifc keyword.

**`Syntax: apropos <keyword>`**
```
$ apropos modpr
```
