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

*Example:*
```
[user@john ~/lecture1]$
[user@john ~/lecture1]$ cd
[user@john ~]$
```
In order to use ```cd``` on a directory do:

```cd {DIRECTORY_PATH}```

*Example:*
```
[user@john ~/lecture1]$ ls
Hello.class Hello.java messages README
[user@john ~/lecture1]$ cd messages/
[user@john ~/lecture1/messages]$
```
What happens if you use ```cd``` on something that **isn't** a directory? Simple, it will just prompt an error.

*Example:*
```
[user@john ~/lecture1]$ ls
Hello.class Hello.java messages README
[user@john ~/lecture1]$ cd README
bash: cd: README: Not a directory
[user@john ~/lecture1/]$
```

## Command - 
