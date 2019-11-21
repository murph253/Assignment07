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


## Summary
