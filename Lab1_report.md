# LAB 1 Report

## cd
**list an example of using the command with no arguments:** 

Command and output: \
[user@sahara ~]$ cd \
[user@sahara ~]$ pwd \
/home

1. When the command was run, I was in the home directory.
2. The reason why I got that output is that when I use the command with no arguments, it
changes my current working directory to my home directory. It is a convention to help users
navigate back to the home directory.
3. The output is not an error.
   
**list an example of using the command with a path to a directory as an argument:**

Command and output: \
[user@sahara ~]$ cd ~/lecture1 \
[user@sahara ~/lecture1]$ pwd \
/home/lecture1

1. When the command was run, I was in the lecture1 directory.
2. The reason why I got that output is that when I use the command with the path to a
directory, this changes my current working directory to the corresponding directory.
3. The output is not an error.

**list an example of using the command with a path to a file as an argument:** 

Command and output: \
[user@sahara ~/lecture1]$ cd messages/Hello.java \
bash: cd: messages/Hello.java: No such file or directory 

1. When the command was run, I was still in the lecture1 directory.
2. The reason why I got that output is that when I use the command with the path to a file,
an error occurs.
3. An error occurs because cd changes the working directory, and it expects the path to a
directory, not a file.

## ls
**list an example of using the command with no arguments:** 

Command and output: \
[user@sahara ~]$ cd lecture1 \
[user@sahara ~/lecture1]$ ls \
Hello.class Hello.java messages README

1. When the command was run, I was in the lecture1 directory.
2. The reason why I got that output is that when I use the command with no argument, it
lists the content in the current working directory.
3. The output is not an error.
   
**list an example of using the command with a path to a directory as an argument:**

Command and output: \
[user@sahara ~/lecture1]$ ls messages \
en-us.txt es-mx.txt zh-cn.txt 

1. When the command was run, I was in the lecture1 directory.
2. The reason why I got that output is that when I use the command with the path to a directory,
it lists the content in the corresponding directory.
3. The output is not an error.

**list an example of using the command with a path to a file as an argument:** 

Command and output: \
[user@sahara ~/lecture1]$ cd messages \
[user@sahara ~/lecture1/messages]$ ls en-us.txt \
en-us.txt

1. When the command was run, I was in the messages directory.
2. The reason why I got that output is that when I use the command with the path to a file, it lists
the name of the file.
3. The output is not an error and it shows the information about that file, including its name.

## cat
**list an example of using the command with no arguments:** 

Command and output: \
[user@sahara ~]$ cat \
hello \
hello

1. When the command was run, I was in the home directory.
2. The reason why I got that output is that when I use the command with no arguments, it waits
for the user to provide the input from the keyboard.
3. The output is not an error.

**list an example of using the command with a path to a directory as an argument:**

Command and output: \
[user@sahara ~]$ cd lecture1 \
[user@sahara ~/lecture1]$ cat messages \
cat: messages: Is a directory

1. When the command was run, I was in the lecture1 directory.
2. The reason why I got that output is that when I use the command with the path to a
directory, an error occurs.
3. The output is an error because ‘cat’ is designed to work with files, not directories.

**list an example of using the command with a path to a file as an argument:**

[user@sahara ~]$ cat messages/zh-cn.txt \
你好世界

1.When the command was run, I was in the lecture 1 directory.
2.The reason why I got that is out put is that when I use the path to a file, it displays the content of that file.
3.The output is not an error.





