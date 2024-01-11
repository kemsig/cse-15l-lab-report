# Lab Report 1 - **Remote Access and FileSystem** *(Week 1)* 
## Context
Below is the file system we are referring to.
```
Home
└── lecture1
    ├── Hello.class
    ├── Hello.java
    ├── messages
    │   ├── en-us.txt
    │   ├── es-mx.txt
    │   └── zh-cn.txt
    └── README
```
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

What happens when you use ```ls``` on a directory path? It will list out all of the *non-hidden* files in that specific directory.
```
[user@john ~/lecture1]$ ls
en-us.txt en-mx.txt zh-cn.txt
```

What happens if you use ```ls``` on something that **isn't** a directory? It will just list that specific file.
```
[user@john ~/lecture1]$ ls Hello.java
Hello.java
```


## Command - Concatenate ```cat```
Using ```cat``` with no arguments will result in the terminal asking for user input, this user input will be echo'd back to the user. In order to exit this mode use the key-combination ```Ctrl+C```.

*note: the blank space is the terminal asking for user input*
```
[user@john ~/lecture1]$ cat

```
*Example when the user gives input.*
```
[user@john ~/lecture1]$ cat
Hello
Hello
woah
woah
^C
[user@john ~/lecture1]$
```

What happens when you use ```cat``` on a directory path? It will prompt an error.
```
[user@john ~/lecture1]$ cat messages/
cat: messages/: Is a directory
```

What happens if you use ```cat``` on something that **isn't** a directory (using it on a file)? It will print out all of the text contents of that file onto the terminal.
```
[user@john ~/lecture1]$ cat Hello.java
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOException {
    String content = Files.readString(Path.of(args[0]), StandardCharsets.UTF_8);    
    System.out.println(content);
  }
}
[user@john ~/lecture1]$
```
[Go back?](https://kemsig.github.io/cse-15l-lab-report/)
