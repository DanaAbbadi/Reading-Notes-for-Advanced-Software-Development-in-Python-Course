# Classes and Objects

Python is an object oriented programming language. Unlike procedure oriented programming, where the main emphasis is on functions, object oriented programming stresses on objects.

An object is simply a collection of data (variables) and methods (functions) that act on those data.

A class is a user-defined constructor or prototype from which objects are created. Classes provide a means of bundling data and functionality together. Creating a new class creates a new type of object, allowing new instances of that type to be made. Each class instance can have attributes attached to it for maintaining its state. Class instances can also have methods (defined by its class) for modifying its state.

## Creating Classes

The *class* statement creates a new class definition. The name of the class immediately follows the keyword class followed by a colon as follows:

     class ClassName:
        variable = 'blah'

        def function(self):
            print("This is a message inside the class.") 

To create an object:

    myobjectx = MyClass()

## Accessing Object Variables

You access the object's attributes using the dot operator with object. Class variable would be accessed using class name as follows:

    myobjectx.variable = 'wow'


# Thinking Recursively in Python

![img](https://files.realpython.com/media/Thinking-Recursively-in-Python_Watermarked.1825397c00ea.jpg)

Recursion is a common mathematical and programming concept. It means that a function calls itself. This has the benefit of meaning that you can loop through data to reach a result.

This means that the function will continue to call itself and repeat its behavior until some condition is met to return a result. All recursive functions share a common structure made up of two parts: base case and recursive case.

Behind the scenes, each recursive call adds a stack frame (containing its execution context) to the call stack until we reach the base case. Then, the stack begins to unwind as each call returns its results.

Recursive functions are common in computer science because they allow programmers to write efficient programs using a minimal amount of code. The downside is that they can cause infinite loops and other unexpected results if not written properly.


# Python Testing with pytest: Fixtures and Coverage

![img](https://quality.studio/wp-content/uploads/2020/05/Screen-Shot-2020-05-22-at-8.36.34-AM.png)

Pytest is a robust Python testing tool, pytest can be used for all types and levels of software testing. pytest can be used by development teams, QA teams, independent testing groups, individuals practicing TDD, and open source projects. In fact, projects all over the Internet have switched from unittest or nose to pytest, including Mozilla and Dropbox. Why? Because pytest offers powerful features such as ‘assert‘ rewriting, a third-party plugin model, and a powerful yet simple fixture model that is unmatched in any other testing framework.

## Fixtures

If your tests need to work on data you typically need to set them up. This is often a process that has to be repeated and independent for each test. This often leads to duplicate code.

The @pytest.fixture decorator provides an easy yet powerful way to setup and teardown resources. You can then pass these defined fixture objects into your test functions as input arguments.

In pytest, you define fixtures using a combination of the pytest.fixture decorator, along with a function definition. For example, say you have a file that returns a list of lines from a file, in which each line is reversed:

    def reverse_lines(f):
        return [one_line.rstrip()[::-1] + '\n'
           for one_line in f]

If you're going to test this function, you'll need to pass it a file-like object. But rather you can create a fixture that'll provide your test with the appropriate object at the right time.

    @pytest.fixture
        def simple_file():
            return StringIO('\n'.join(['abc', 'def', 'ghi', 'jkl']))




