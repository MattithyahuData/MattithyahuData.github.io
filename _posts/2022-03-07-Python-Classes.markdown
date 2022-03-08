---
layout: post
title:  "Article: Python Classes and Objects"
date:   2022-03-07 16:30:58 +0100
categories: jekyll update
---

### How and when to use classes?  

#### *What is Object-oriented programming (OOP)?* OOP is a procedural programming technique that organises code design around data, or objects, rather than functions and logic. 

*"Python is an object-oriented programming language. Everything is in Python treated as an object, including variable, function, list, tuple, dictionary, set, etc. Every object belongs to its class."*

<img src="images/classimage.jpg"/>

<br>
<br>

*What is a function?* A function is a set of code that performs specific task(s) when called. They are called functions in programming languages like Python, R, and C++ and 'Macros' in SAS.

Functions begin with the 'def' keyword to create a function. The first string inside the class is called a docstring and has a brief description of the class and or function. Although not mandatory, this is highly recommended. *DocStrings can also be used to record variable and data information for input into both functions and classes.
Functions cannot be empty, but if you for some reason have a function with no content, put in the pass statement to avoid getting an error. Pass is like a null operation used as a placeholder for future code, nothing is executed with the Pass statement. 

```python
# Basic Function creation
def NewFunction():
    '''Basic Function'''
    pass

# Calling NewFunction
NewFunction()
```
*   Function to print "Hello World!"

```python
# Basic Function creation
def NewFunction():
    '''Basic NewFunction'''
    print("Hello World!")

# Calling NewFunction
NewFunction()

## Output ## 
Hello World!
```

***What is a class?*** <br>
A class is a construction sequence for the creation or object it acts as the "blueprint" for creating objects.

***What is an object?*** <br>
An object is a unique instance of a data structure that is defined by its class. 

## Defining a new class

Like function definitions begin with the 'def' keyword in Python, class definitions begin with the keyword 'class'.

Class definitions too cannot be empty, so as above with functions the 'Pass' statement is used to avoid getting an error. 
```python
# Basic Class creation 
class NewClass:
    '''Basic NewClass'''
    pass
```

Using class to print value x
```python
# Creating new class
class TestClass:
    '''Basic Class'''
    x = 10
    
# Using class to create objects to print the value of x
obj = TestClass()

# Printing variable x within object: obj
print(obj.x)

## Output ## 
10
```

All classes have a function called __init__(), which is always executed when the class is being initiated. It is hidden unless you instantiate it. 
This function can be used to assign values to object properties 
**The __init__() function is called automatically every time the class is being used to create a new object.**

*   Objects can also contain methods. Methods in objects are functions that belong to the object. Methods are used in a class. 
*   The self parameter is a reference to the current instance of the class, and is used to access variables that belongs to the class.
It can be named anything and does not have to be 'self', but it must be the first parameter in the __init__() function 

```python
# Creating new class
class Personinfo:
    '''Basic Class'''

    # Defining __init__ function 
    def __init__(self, fname, lname, age):

        # Using self to set name and age 
        self.fname = fname
        self.lname = lname
        self.age = age

    # Function to print input name when called 
    def myfunc(self):
        ''''''
        # From the class input this instance method prints a sentence | Age variable converted to string for concatenation 
        print("Hello my name is " + self.fname + " " + self.lname + "and I am " + str(self.age))

# Using class to create object 
personinfo_obj = Personinfo("John","Doe",30)

# Calling instance function within class to get output 
personinfo_obj.myfunc()

## Output ## 
Hello my name is John Doeand I am 30
```

Thanks for making it to the end of this tutorial style article.

## Questions | Contact me 
For questions, feedback, and contribution requests contact me
* ### [Click here to email me](mailto:contactmattithyahu@gmail.com) 
* ### [See more work here](https://mattithyahudata.github.io/)

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
