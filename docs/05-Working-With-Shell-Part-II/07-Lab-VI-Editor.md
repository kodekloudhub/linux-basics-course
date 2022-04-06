# Lab - VI Editor

- Access Hands-On Labs here [Hands-On Labs](https://kodekloud.com/topic/lab-vi-editor-3/)

Go to **`insert mode`**
```
Press i
```

Exit from **`insert mode`** and go to **`command mode`**
```
Press ESC
```

To **`remove`** a character
```
Move Cursor to the characters to be removed and press x to remove them
```

Change the file contents to **`Welcome to KodeKloud`** and **`save`** file.
```
Go to insert mode by pressing i and delete all content and type in new content. Once done press ESC key and go to command mode. Then type in command :w!
```

Update the port it listens on from **`80`** to **`5000`** in apache webserver.
```
Go to insert mode by pressing i and replace 80 with 5000 in line 10
```

Remove the line that starts with **`LogFormat`**.
```
Go to the line 33 and press dd (d twice) to remove the entire line.
```

To undo the previous change
```
Press u to undo previous change
```

There's a 6 hiding in the file. Find it.
```
find command /6
```

