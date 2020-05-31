# Different types of Shells

In this section, we will take a look at different types of shells.
- There are different types of shells in linux, some of the popular ones are below
  - Bourne Shell (sh)
  - C Shell (csh or tsh)
  - Korn Shell (ksh)
  - Z Shell (zsh)
  - Bourne again shell (Bash)
  
To check the shell being used. Use the command **`echo $SHELL`**
```
$ echo $SHELL
```

To change the default shell. Use the command chsh, you will be prompted for the password and following that input the name of the new shell. You have to login into new terminal session to see this change though.
```
$ chsh
```

## Bash Shell Features

1. Bash supports command auto-completion. What this means is bash means to auto-complete commands for you if you type part of it and press the **`tab`** key
   
   ![bash-auto](../../bash-auto.PNG)
   ![bash-auto1](../../bash-auto1.PNG)
