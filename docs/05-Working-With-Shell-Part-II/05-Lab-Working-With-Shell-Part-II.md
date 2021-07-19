# Lab - Working With Shell Part - II

- Access Hands-On Labs here [Hands-On Labs](https://kodekloud.com/topic/lab-working-with-shell-ii/)

Create a tarball of the directory called **`python`** and compress it using **`gzip`**. The compressed tar file should be available at **`/home/bob/python.tar.gz`**
```
$ tar -cf /home/bob/python.tar /home/bob/reptile/snake/python
$ gzip /home/bob/python.tar
```

There is a compressed file called eaglet.dat.gz located under the eagle directory. Extract it in the same location
```
$ gunzip /home/bob/birds/eagle/eaglet.dat.gz
```

A file has been copied to the laptop by the name of caleston-code. But he does not remember which directory he saved it in.Can you find it?
```
$ sudo find / -name caleston-code
```

Find the location of the file called **`dummy.service`** and redirect its absolute path to the file **`/home/bob/dummy-service`**. You can use the redirect operator with the echo command to save the answer to the file.
```
$ sudo find / -name dummy.service
$ echo /etc/systemd/system/dummy.service > /home/bob/dummy-service 
```

Find the file under **`/etc`** directory that contains the string **`172.16.238.197`**. Save the answer using the absolute path in the file **`/home/bob/ip**`
```
$ sudo grep -ir 172.16.238.197 /etc/ > /home/bob/ip
```

Create a new file called **`/home/bob/file_wth_data.txt`**. This file should have one line of text that says **`a file in my home directory`**. Make use of the redirect operator.
```
$ echo "a file in my home directory" > /home/bob/file_wth_data.txt
```

Run the command python3 **`/home/bob/my_python_test.py`** and redirect the **`standard error`** to the file **`/home/bob/py_error.txt`**.
```
$ python3 /home/bob/my_python_test.py 2>/home/bob/py_error.txt
```

Read the file **`/usr/share/man/man1/tail.1.gz`** and without extracting it copy the first line of this file to **`/home/bob/pipes`**
```
$ zcat /usr/share/man/man1/tail.1.gz | head -1 > /home/bob/pipes
```

