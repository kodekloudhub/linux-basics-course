# ACCESS CONTROL FILES

  - Take me to the [Tutorial](https://kodekloud.com/topic/access-control-files/)
  
  - Access Ccontrol files are stored under **`/etc`**.
  - Can be read by anyone and can be only edited by **`root`** user.


  ### Control files

  - To get more details about one's account for example **`bob`** account, home director, uid, and shell check **`/etc/passwd`** 

    ```
    [~]$ grep -i ^bob /etc/passwd
    bob:x:1002:1002::/home/bob:/bin/sh
    USERNAME:PASSWORD:UID:GID:GECOS:HOMEDIR:SHELL
    ```
   
    ![passwd](../../images//passwd.PNG)

  - Password are stored under **`/etc/shadow`**

    ```
    [~]$ grep -i ^bob /etc/shadow
    bob:$6$0h0utOtO$5JcuRxR7y72LLQk4Kdog7u09LsNFS0yZPkIC8pV9tgD0wXCHutY
    cWF/7.eJ3TfGfG0lj4JF63PyuPwKC18tJS.:18188:0:99999:7:::

    USERNAME:PASSWORD:LASTCHANGE:MINAGE:MAXAGE:WARN:INACTIVE:EXPDATE
    ```

    ![shadow](../../images//shadow.PNG)

  - Check the groups **`bob`** belongs too

    ```
    [~]$ grep -i ^bob /etc/group
    NAME:PASSWORD:GID:MEMBERS
    ```

    ![egp](../../images//egp.PNG)

# HANDS-ON LABS

  - Lets start with Managing and User Accounts [here](https://kodekloud.com/courses/the-linux-basics-course/lectures/17074503)