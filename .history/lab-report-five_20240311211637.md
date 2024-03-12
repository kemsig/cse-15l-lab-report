# Lab Report 5 - Putting it All Together (Week 9)

## Part 1 – Debugging Scenario

## *Students Post.*

**Title:**
Getting A Blank Line When Running Sort Algorithm.

**Description**
Hey so I made a program where I am testing out the sorting algorithm, insertion sort. And when I run my bash script to run the file ```run.sh``` it outputs the unsorted array followed by blank text. Also after I launch this it seems that I cant type anything into the terminal anymore! Below I have provided The output I got along with the content of my code and my file structure. Thank you!

*Output:*

![bugoutput](Images/report5/Screenshot%202024-03-11%20200352.png)

*My File Structure:*

![fs](Images/report5/Screenshot%202024-03-11%20200034.png)

*My Code for ```SortingAlgo.java```:*

![](Images/report5/Screenshot%202024-03-11%20200831.png)

*My Code for ```run.sh```:*

![](Images/report5/Screenshot%202024-03-11%20201020.png)

## *Instructional Assistant Response.*

Hey Kayne! After careful review I can see that your ```run.sh``` file is working just fine. I am speculating that there is **something wrong with the file** ```SortingAlgo.java```.

The problem that you encountered where you weren't able to access the terminal and only part of your code ran was because of an **infinite loop**.

Because the first two lines being printed out in the terminal that means the program was running fine until we reach the line calling the function ```insertionsort(testArr)```. This means that the infinite loop is happening in this function.
```
System.out.println("Unsorted."); // line 1
printArray(testArr); //line 2

// Print out  the sorted Array.
insertionsort(testArr); // Where the error is occurring.
```

In order to see where the infinite loop is occurring we can use ```jdb``` the **java debugger** to find out. You can do this by doing the following steps:

Compile ```SortingAlgo.java``` with the ```-g``` flag just in case we need to see any debugging information.
```
javac -g SortingAlgo.java
```

Next we enter the **java debugger** on the compiled file by doing:
```
jdb SortingAlgo
```

Once we enter the ```jdb``` we can ```run``` the program to see that we encounter an **infinite loop**.
```
run
```

After gauging that we have an infinite loop we can ```suspend```  the program to start our analysis.
```
suspend
```

Find the thread for the **main function** because this is likely where the program is running.
```
threads
```

The thread should've been in the group **main**. Also the thread will likely be called ```0x1``` since I've seen that you are on the ```ieng6``` machine. Now we will dump the threads **stack**.  If you remember the stack is where functions are loaded. We can dump it by doing:
```
where <thread>
```

Now we can ```step``` through the file to see where the infinite loop is occurring. Do this a couple of times to see where in the program that we are stuck.
```
step
```

Now that you've found this out go to the line number and figure and edit the part in your code that is making your program encounter the infinite loop!

Another quick tip is that if you end up using ```vim``` to find and fix the bug you can use these two commands to find where it is easier:

See what line number you are on:
```
:set number
```

Jump to a specific line:
```
:<line number>

#Example of jumping to line 4
:4 
```

Hope this helps!

## *Students Reply.*

Thank you for the reply. I have followed your steps below and I have fixed my bug! Here is my process.

First I had compiled my program with the ```-g``` flag and it was successful.
![comp](image.png)

Next I entered ```jdb```.

![alt text](image-1.png)

Now that I was in here I had ran the program with ```run```.

![alt text](image-2.png)

I saw that I encountered the infinite loop that you were talking about and now understand this is why my program isn't completing. So in order to dissect what as going wrong I took your advice and used the ```suspend``` command.

![alt text](image-3.png)

Now that the program has stopped I tried to find the **main thread** like you said using the ```threads``` comand.

![alt text](image-4.png)

I see that the main thread is at ```0x1``` like you said so I next tried to see what was going on in the stack using the ```where``` command on the thread ```0x1```.

![alt text](image-5.png)

I can see my function ```insertionsort``` is stuck is on the stack frame. So now I know there is something wrong with it because when a program completes the stack should become empty. So I next started to use the ```step``` command to go through the program to see where the infinite loop is occurring.

![alt text](image-6.png)

After this I can see that **my bug is** that the program is getting stuck on lines 10-11 because of an **infinite loop** on the ```while``` loop. I used ```vim``` to enter the file and used the ```vim``` command ```:10``` to jump to line number 10 to see what was going wrong and used ```:set number``` to see what line I am on.

![alt text](image-7.png)

I see that the bug is happening on this ```while``` loop. After carefully taking a look I figured out that I forgot to decrement the variable ```k```. I added ```k--``` after line 11 to see if it would fix this.

This is the change that I made.

![alt text](image-8.png)

Now after saving with ```:x``` I had run the bash script ```run.sh``` to see if it would work.

![alt text](image-9.png)

Now my program is successfully debugged and works! Thanks to you I learned what an infinite loop was, how to diagnosis it with ```jdb```, and how to fix it!

## Part 2 – Reflection

One cool thing I learned through this course is the the *java debugger* or the command ```jdb```. Beforehand I would use a series of ```System.out.println()``` in order to see what parts of my code is being accessed. It was very time consuming and sometimes didn't even help me find out what my bug was. Now that we have learned how to use the ```jdb``` I now know I can do these ```print``` commands through the terminal and can even do more like using ```step``` to go through the program line by line. Using ```locals``` to print out the values of all of the local variables that are being used, which without the debugger I would've just put a ton of ```print``` statements on every single variable. Overall the ```jdb``` is a tool that I will continue to use in order to debug my programs.