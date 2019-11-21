# Error Handling and Pickles
**Dev:** *JMurphy*
**Date:** *11.14.2019*


## Introduction
In Python, there is a vast list of pre-defined modules. Think of a module as simply a file containing Python code. That module can execute a myriad of actions such as defining functions, classes and variables. You can even create your own module to be called at a later time using the "import" statement. 

For this assignment, we will be using the pickle module. Yes it is bitter sweet, but no it's not edible. I will discuss the advantages and disadvantages of importing pickle as well as screen shots of the pickle module in use, and how it obscures your data. We will also be going over exception and error handling, their definitions, and why you shouldn't get upset when you encounter them. 

## I got a Pickle, I got a Pickle, I got a Pickle hey hey hey hey!
What is pickling in python? Why should I use it? Why shouldn’t I? These are some of the questions that have been raised since the dawn of time. Okay, maybe they haven’t, but I know I asked all of these questions myself and I’m sure I’m not alone. I will try my best to explain. 

### What is pickling?
Pickling takes your data and converts it into a byte stream. What’s a byte stream? A byte is a unit of data that is eight binary digits long (or eight bits long, e.g. 0 1 0 0 1 1 0 1). It’s also incredibly effective at serializing and de-serializing object structures. 

### Advantages of pickling
The website GeeksforGeeks.org states three main advantages for using the pickle module:
1.Recursive objects: Pickle keeps track of the objects it has already serialized, so later references to the same object won't be serialized again.
2. Object Sharing: this is similar to self-referencing objects; pickle stores the object once, and ensures that all other references point to the master copy.
3. User-defined classes and their instances: Marshal does not support these. Pickle can save and restore class instances transparently. the class definition must be importable and live in the same module as when the object was stored.

### Disadvantages of pickling
The pickle module is UN-SECURE! I say again UN-SECURE! A Google search on pickle modules is always paired with an advisory to how it's unsecure. Another downfall is that pickle is both slower and produces larger serialized values than most of the alternitives (https://www.benfrederickson.com/dont-pickle-your-data/). There may also be some instances where non-python programs may not be able to reconstruct pickled Python objects. 

### A Pickle demonstration
Below is basic demonstration of a program that demonstrates pickle. 

```
# ------------------------------------------------- #
# Title: Pickle Demonstration
# Description: A simple example of storing data in a binary file
# ChangeLog: (Who, When, What)
# JMurphy,11.20.2030,Completed Script for Assignment 07
# ------------------------------------------------- #

import pickle
strfirstName = str(input("Enter a First Name: "))
strlastName = str(input("Enter a Last Name: "))
intlastFour= int(input("Enter Last Four of SSN Number: "))
lstuserData = [strlastName, strfirstName, intlastFour]


# Now we store the data with the pickle.dump method
objFile = open("nameLine.dat", "ab")
pickle.dump(lstuserData, objFile)
objFile.close()

# And, we read the data back with the pickle.load method
objFile = open("nameLine.dat","rb")
objFileData = pickle.load(objFile)
objFile.close()
print(objFileData)
```

Here is the output to the above code:

![Results of Pickle](https://github.com/murph253/Assignment07/blob/master/docs/Figure%201.1.PNG "Results of Pickle")

When you open the file where you pickled your objects, it will look like the following when opened:

![Pickle Contents](https://github.com/murph253/Assignment07/blob/master/docs/Figure%201.2.PNG "Pickle Contents")

The pickle module saved my data into a byte string and into a serialized object structure. The appearance of the file would lead some to belive that this file is now secure, but its important to remember that you should never open a pickled file from an untrusted source!

## Errors and Handling Exceptions
The two most distinguishable kinds of errors are syntax and exceptions. A syntax error occurs when Python is unable to understand a line of code, they are almost always fatal. The good thing is that most syntax errors are just typos or incorrect indents. These are all highlighted and called to your attention in PyCharm or IDLE. There really is no way around these errors, so stay on the lookout. Because these errors are highlighted and pointed out to you in PyCharm or IDLE, we don't need to discuss them as much as exceptions and handling ex

Exceptions are errors that are detected during execution and can be written into your own Python programs. Some common types of exceptions are NameError, ValueError and TypeError. Have you ever inputted a string into an integer input? If you have you probably encoutered a ValueError. 

Exceptions and Errors are nothing to be ashamed of. It happens to all of us. It's important to understand them not only for your sanity but to assist your programs and your ability to grow as a programmer. 

### Exception Handling
I can’t stress enough how an exception can help you navigate your code easier. As stated above, an exception is not fatal and if you can catch a potential exception before it gives an error, you just earned yourself a gold star! Why? Because I am the author and I said so, but also because you're no longer in the crawl phase of Exception Handling, and you are in some sort of a more mobile phase, maybe a sprint, maybe a jog, either way let's get you moving! 

Exception handling allows you to deal with errors in your own way. It allows the programmer to decide what happens when someone inputs a multiplication sign in an integer input. Instead of throwing an error, you could provide a custom message that details what the user needs to do to move forward. There goes that movement reference again! 

If you have a portion of code that requires strict inputs, you should use the 'try' block. Below is a very simple example of an exception error and how I used the try block to handle it. 


```
try:
    file = open("SecretFileWithMillionsInBitCoin", "rb")
except FileNotFoundError as facePalm:
    print("I’m sorry, it appears you lost your millions!!")
    print(facePalm, facePalm.__doc__, type(facePalm), sep='\n')
```

This is what it looks like in cmd.

![Millions Lost](https://github.com/murph253/Assignment07/blob/master/docs/Figure%202.1.PNG "Millions Lost")

Another example, this time a value error handled by the try under the while true block!

```
while True:
    try:
        firstName = str(input("Please enter your first name: "))
        lastName = str(input("Please enter your last name: "))
        phoneNum = int(input("Please enter your phone number: "))
        break
    except ValueError:
        print("ERROR! Please do not include dashes (-) when inputting phone number.”)
```
and its output:


![Sorry Dashes](https://github.com/murph253/Assignment07/blob/master/docs/Figure%202.2.PNG "Sorry Dashes")

## Summary
Syntax errors are showstoppers, but exceptions can be either a complete pain, or a way to guide the user of your program through your program, quickly and successfully. There are hundreds of pages of data regarding the pickle module, errors and exception handling. If you have one takeaway form this document I hope that its how you can incorporate exception handling into your program. 

Here is a list of some great resources I used for this assignment:
http://conquerprogramming.com/blog/3-Exceptions.html
https://docs.python.org/3/tutorial/errors.html
https://www.tutorialspoint.com/python/python_modules.htm
