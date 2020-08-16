# Python Basics

![python](/img/Python.png)

Python is a powerful general-purpose programming language. It is used in web development, data science, creating software prototypes, and so on. Fortunately for beginners, Python has simple easy-to-use syntax. This makes Python an excellent language to learn to program for beginners.

This tutorial is a summary for what I learned through [Learn Python](https://www.learnpython.org) website.

## Variables

Python is completely object oriented, and not "statically typed". You do not need to declare variables before using them, or declare their type. Every variable in Python is an object.

Python supports two types of numbers - integers and floating point numbers.

Strings are defined either with a single quote or a double quotes.

## Lists

Lists are very similar to arrays. They can contain any type of variable, and they can contain as many variables as you wish.

Python has a set of built-in methods that you can use on lists/arrays:

|Method | Description |
|-------|-------------|
| append() | Adds an element at the end of the list |
| clear() | Removes all the elements from the list |
| copy() | Returns a copy of the list |
| count() | Returns the number of elements with the specified value |
| extend() | Add the elements of a list (or any iterable), to the end of the current list |
| index() | Returns the index of the first element with the specified value|
| insert() | Adds an element at the specified position|
| pop() | Removes the element at the specified position|
| remove() | Removes the first item with the specified value |
| reverse() | Reverses the order of the list|
| sort() | Sorts the list |

## String Formatting

Python uses C-style string formatting to create new, formatted strings. The "%" operator is used to format a set of variables enclosed in a "tuple" (a fixed size list), together with a format string, which contains normal text together with "argument specifiers", special symbols like "%s" and "%d".

Example:

    ``` 
        name = "John"
        print("Hello, %s!" % name)

        # This prints out "John is 23 years old."
           name = "John"
           age = 23
           print("%s is %d years old." % (name, age))

    ``` 

Any object which is not a string can be formatted using the %s operator as well.

Here are some basic argument specifiers you should know:

- %s - String (or any object with a string representation, like numbers)
  
- %d - Integers

- %f - Floating point numbers

- %.< number of digits>f - Floating point numbers with a fixed amount of digits to the right of the dot.

- %x/%X - Integers in hex representation (lowercase/uppercase)

## Conditions

### IF...ELIF...ELSE Statements

An ***else*** statement can be combined with an if statement. An else statement contains the block of code that executes if the conditional expression in the if statement resolves to 0 or a FALSE value.

The else statement is an optional statement and there could be at most only one else statement following if.

Syntax:

    ```
    if expression:
        statement(s)
   else:
        statement(s)
    ```

The ***elif*** statement allows you to check multiple expressions for TRUE and execute a block of code as soon as one of the conditions evaluates to TRUE.

Similar to the else, the elif statement is optional. However, unlike else, for which there can be at most one statement, there can be an arbitrary number of elif statements following an if.

### Boolean operators

The "and" and "or" boolean operators allow building complex boolean expressions, for example:

    ```
name = "John"
age = 23
if name == "John" and age == 23:
    print("Your name is John, and you are also 23 years old.")

if name == "John" or name == "Rick":
    print("Your name is either John or Rick.")
    ```

### The "in" operator

The "in" operator could be used to check if a specified object exists within an iterable object container, such as a list:

    ```
    name = "John"
    if name in ["John", "Rick"]:
        print("Your name is either John or Rick.") 
    ```

Python uses indentation to define code blocks, instead of brackets. The standard Python indentation is 4 spaces, although tabs and any other space size will work, as long as it is consistent. Notice that code blocks do not need any termination.

### The "is" operator

The is operator compares the identity of two objects while the == operator compares the values of two objects. There is a difference in meaning between equal and identical. And this difference is important when you want to understand how Python's is and == comparison operators behave.

The == operator is used when the values of two operands are equal, then the condition becomes true.

The is operator evaluates to true if the variables on either side of the operator point to the same object and false otherwise.

### The "not" operator

Using "not" before a boolean expression inverts it.

## Loops

### For loop

Syntax:

    ```
    fruits = ["apple", "banana", "cherry"]
    for x in fruits:
        print(x)
    
    for x in "banana":
        print(x)

    ```

#### The break Statement

With the break statement we can stop the loop before it has looped through all the items:

    ```
    fruits = ["apple", "banana", "cherry"]
    for x in fruits:
      print(x)
      if x == "banana":
         break
    ```

### "while" loops

While loops repeat as long as a certain boolean condition is met. For example:

    ```

    count = 0
    while count < 5:
        print(count)
        count += 1  # This is the same as count = count + 1

    ```

## Functions

Functions in python are defined using the block keyword "def", followed with the function's name as the block's name. For example:

    ```
    def my_function(username, greeting):
        print("Hello, %s , From My Function!, I wish you %s" %(username, greeting))

        a,b=1,2
        return a + b
    ```

**How do you call functions in Python?**

 Simply write the function's name followed by (), placing any required arguments within the brackets. For example, lets call the functions written above (in the previous example):

    ```
    my_function_with_args("John Doe", "a great year!")

    ```
