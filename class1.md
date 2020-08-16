# Big O Notation

![img](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcRhqOQolF0deDqQXUK-GtKQbm5eM6ywwVL7aQ&usqp=CAU)

**Big O notation** is a convenient way to describe how fast a function is growing. When we compute the time complexity T(n) of an algorithm we rarely get an exact result, just an estimate. That’s fine, in computer science we are typically only interested in how fast T(n) is growing as a function of the input size n.

For example, if an algorithm increments each number in a list of length n, we might say: “This algorithm runs in O(n) time and performs O(1) work for each element”.

## O(1)

O(1) describes an algorithm that will always execute in the same time (or space) regardless of the size of the input data set.

## O(N)

O(N) describes an algorithm whose performance will grow linearly and in direct proportion to the size of the input data set.

## O(N2)

O(N2) represents an algorithm whose performance is directly proportional to the square of the size of the input data set.

## O(2N)

O(2N) denotes an algorithm whose growth doubles with each additon to the input data set.

# Python names and values

![img](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcTq_uRFiWq_iWdNcNXmZvik_Ncm4MRWF3wytg&usqp=CAU)

The behavior of names and values in Python can be confusing. Like many parts of Python, it has an underlying simplicity that can be hard to discern, especially if you are used to other programming languages.

As in many programming languages, a Python assignment statement associates a symbolic name on the left-hand side with a value on the right-hand side. In Python, we say that names refer to values, or a name is a reference to a value

Assigning a value to a name never copies the data, it never makes a new value. Assignment just makes the name on the left refer to the value on the right.

Values fall into two categories based on their type: mutable or immutable. Immutable values include numbers, strings, and tuples. Almost everything else is mutable, including lists, dicts, and user-defined objects. Mutable means that the value has methods that can change the value in-place. Immutable means that the value can never change, instead when you think you are changing the value, you are really making new values from old ones.

Python is dynamically typed, which means that names have no type. Any name can refer to any value at any time. A name can refer to an integer, and then to a string, and then to a function, and then to a module.

Just as names have no type, values have no scope. When we say that a function has a local variable, we mean that the name is scoped to the function: you can’t use the name outside the function, and when the function returns, the name is destroyed. But as we’ve seen, if the name’s value has other references, it will live on beyond the function call. It is a local name, not a local value.
