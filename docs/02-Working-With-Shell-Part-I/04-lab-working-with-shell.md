# Lab - Working with shell

- Access Hands-On Labs here [Hands-On-Labs](https://kodekloud.com/topic/lab-working-with-the-shell/)

1. To check the home directory for a particular user say **`bob`**
   ```
   $ grep bob /etc/passwd | cut -d ":" -f6
   ```
1. To check the home directory for a particular user using built in shell variables
   ```
   $ echo $HOME
   ```
1. In the command **`echo Welcome`**, what does the word Welcome represent with respect to the command?
   ```
   $ echo Welcome 
     - Where Welcome is an argument
   ```
   
1. To check **`git`** command type
   ```
   $ type git
   ```
1. To create a directory
   ```
   $ mkdir /home/bob/birds
   ```
1. To create directories recursively
   ```
   $  mkdir -p /home/bob/fish/salmon
   ```
1. Create few more directories
   ```
   $ mkdir -p /home/bob/mammals/elephant
   $ mkdir -p /home/bob/mammals/monkey
   $ mkdir /home/bob/birds/eagle
   $ mkdir -p /home/bob/reptile/snake
   $ mkdir -p /home/bob/reptile/frog
   $ mkdir -p /home/bob/amphibian/salamander
   ```
1. To move a directory
   ```
   $ mv /home/bob/reptile/frog /home/bob/amphibian
   ```
1. To rename a directory
   ```
   $ mv /home/bob/reptile/snake /home/bob/reptile/crocodile
   ```
1. To delete a directory
   ```
   $ rm -r /home/bob/reptile
   ```
