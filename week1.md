# Lab Report 1 - **Remote Access and FileSystem** *(Week 1)* 
## Context
File system.
>Home
>> lecture1
>>> messages
>>> > en-us.txt
>>> > zh-cn.txt

## Command - **Change Directory** (```cd```)
Using ```cd``` with no arguments should bring you back to your home directory.
```
[user@john ~/lecture1]$
[user@john ~/lecture1]$ cd
[user@john ~]$
```

What happens when you use ```cd``` on a directory path? It will just switch your working directory into the specified directory.
```
[user@john ~/lecture1]$ cd messages/
[user@john ~/lecture1/messages]$
```
What happens if you use ```cd``` on something that **isn't** a directory? Simple, it will just prompt an error.
```
[user@john ~/lecture1]$ cd README
bash: cd: README: Not a directory
[user@john ~/lecture1/]$
```

## Command - List ```ls```
Using ```ls``` with no arguments should list out all of the *non-hidden* files in your current working directory.
```
[user@john ~/lecture1]$ ls
Hello.class Hello.java messages README
```
What happens when you use ```cd``` on a directory path? It will just switch your working directory into the specified directory.
What happens if you use ```cd``` on something that **isn't** a directory? Simple, it will just prompt an error.

## Command - List ```ls```
Using ```cd``` with no arguments should bring you back to your home directory.
What happens when you use ```cd``` on a directory path? It will just switch your working directory into the specified directory.
What happens if you use ```cd``` on something that **isn't** a directory? Simple, it will just prompt an error.
