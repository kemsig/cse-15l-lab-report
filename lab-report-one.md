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
The command ```cd``` stands for **Change Directory**. It's functionality is that it changes the current *working directory* into the one specified.

You can use it by typing in the following.
*Note: replace ```<directory>``` with the specific directory you are trying to change into.*
```
cd <directory>
```
Using ```cd``` with no arguments should bring you back to your home directory. **(NOTE THIS WILL ONLY HAPPEN IF YOU ARE ON A UNIX BASED TERMINAL, ex: doesn't work on Windows**)

*The current working directory is:*
```
/home/lecture1
```
*Example:*
```
[user@john ~/lecture1]$
[user@john ~/lecture1]$ cd
[user@john ~]$
```
*Result:*
We had changed into the ```/home``` directory **with no error** from the ```/home/lecture1``` directory and now if we do ```pwd``` we should get the output ```/home```. We had gotten this result because we specific no directory. There had been no error message and our command executed, so there this is not an error. *Extra: if we were to do this on a Windows terminal like Powershell, it wouldn't do anything*.

# 

What happens when you use ```cd``` on a directory path? It will just switch your working directory into the specified directory.

*The current working directory is:*
```
/home/lecture1
```
It's file contents are (*Note: ```messsages``` is a directory*):
```
Hello.class  Hello.java  messages README
```

*Example:*
```
[user@john ~/lecture1]$ cd messages/
[user@john ~/lecture1/messages]$
```
*Result:*
With this command we have now switched into the ```/messages``` directory with **no error**. This had happend because we specificed to switch into the ```/messages``` directory. This isn't an error because there is no error message and the command executed. Now if we run ```pwd```, we can see our working directory is now, ```/home/lecture1/messages```.

# 

What happens if you use ```cd``` on something that **isn't** a directory? Simple, it will just prompt an error because the file specified isn't a directory with file contents.

*Our current working directory is:*
```
/home/lecture1
```

It's file contents are (*Note: ```messsages``` is a directory*):
```
Hello.class  Hello.java  messages README
```

*Example:*
```
[user@john ~/lecture1]$ cd README
bash: cd: README: Not a directory
[user@john ~/lecture1/]$
```
*Result:*
We had failed to switch our directory into ```README``` and had **prompted and error** because it is a **file** and **not a directory**. So the current working directory that we are in is still ```/home/lecture1``` because our ```cd``` command was cancelled.

## Command - List (```ls```)
The command ```ls``` stands for **List**. It's functionality is that it lists all of the files in the current working directory that the user is in.

The following is how you use it. (The argument is optional)
```
ls <directory>
```

Using ```ls``` with no arguments should list out all of the *non-hidden* files in your current working directory.

Our current directory is:
```
/home/lecture1
```

It's file contents are (*Note: ```messsages``` is a directory*):
```
Hello.class  Hello.java  messages README
```

*Example:*
```
[user@john ~/lecture1]$ ls
Hello.class Hello.java messages README
```

*Result:*
We had gotten a list of all of the items in the **current** working directory because we didn't specify any arguments with **no error**. THe files listed out are all of the files in ```/home/lecture1``` because that is the current working directory that we are in. This is not an error as we had no error message and the command executed.

# 

What happens when you use ```ls``` on a directory path? It will list out all of the *non-hidden* files in that specific directory.

*Our current working directory is:*
```
/home/lecture1
```

It's file contents are (*Note: ```messsages``` is a directory*):
```
Hello.class  Hello.java  messages README
```

*Example:*
```
[user@john ~/lecture1]$ ls
en-us.txt en-mx.txt zh-cn.txt
```

*Result:*
Because we had **specified** a directory we had listed all of the files in that directory. In this case we had specified the directory ```messages``` so we get a list of it's file contents. There is no error because there is no error message and it had executed properly. We hadn't switched into any other directory with this command so we are still in ```/home/lecture1```.

# 

What happens if you use ```ls``` on something that **isn't** a directory? It will just list that specific file.

Our current directory is:
```
/home/lecture1
```

It's file contents are (*Note: ```messsages``` is a directory*):
```
Hello.class  Hello.java  messages README
```

*Example:*
```
[user@john ~/lecture1]$ ls Hello.java
Hello.java
```

*Result:*
Because we specified a specific file not a directory, it had printed all of the contents, which is just a **singular file**, so the output was just our input which is ```Hello.java```. This is not an error as there is no error message and the command had executed as expected. We hadn't switched into any other directory with this command so we are still in ```/home/lecture1```.


## Command - Concatenate (```cat```)
The command ```cat``` is short for **Concatenate**. This command can take in several files as arguments (**no directories**) and prints out it's contents into the terminal.

You can use it by typing the following: (can take in multiple args, arg is optional)
```
cat <file_name>
```
# 

Using ```cat``` with no arguments will result in the terminal asking for user input, this user input will be echo'd back to the user. In order to exit this mode use the key-combination ```Ctrl+C```.

Our current directory is:
```
/home/lecture1
```

*Example:*
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

*Result:*
Because we had used the command with no arguments, it had resulted in toggling a mode where it awaits the user to type something, then it echos it back to them. This is not an error as it is how the command is meant to function, there is also no error message, and no exception.

# 

What happens when you use ```cat``` on a directory path? It will prompt an error.

Our current directory is:
```
/home/lecture1
```

*Example:*
```
[user@john ~/lecture1]$ cat messages/
cat: messages/: Is a directory
```

*Result:*
Because we had used the command on the directory ```messages/``` we had received an **error**. We had received this because the ```cat``` command can only take in files as arguments **not directories**.

# 

What happens if you use ```cat``` on something that **isn't** a directory (using it on a file)? It will print out all of the text contents of that file onto the terminal.

Our current directory is:
```
/home/lecture1
```

*Example:*
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

*Result:*
Because we had used the ```cat``` command on a specific file, in this case, ```Hello.java```, it had printed out all of the contents inside that java file. This is not an error this is how the ```cat``` command was meant to work, there is no error message, and the command executed as expected.

[Go back?](https://kemsig.github.io/cse-15l-lab-report/)
