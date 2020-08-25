# List Comprehensions in Python

 List comprehension is an elegant way to define and create lists based on existing lists. Rather than creating an empty list and adding each element to the end, you simply define the list and its contents at the same time by following this format:

    new_list = [expression for member in iterable]

Where,
1. expression is the member itself, a call to a method, or any other valid expression that returns a value.
  
2. member is the object or value in the list or iterable.

3. iterable is a list, set, sequence, generator, or any other object that can return its elements one at a time.

Example:

    [x.lower() for x in ["A","B","C"]]
    # Output: ['a', 'b', 'c']

One main benefit of using a list comprehension in Python is that it’s a single tool that you can use in many different situations. In addition to standard list creation, list comprehensions can also be used for mapping and filtering. You don’t have to use a different approach for each scenario.

### Using Conditional Logic

A more complete description of the comprehension formula adds support for optional conditionals. The most common way to add conditional logic to a list comprehension is to add a conditional to the end of the expression:

    new_list = [expression for member in iterable (if conditional)]

Conditionals are important because they allow list comprehensions to filter out unwanted values

Example:

    num_list = [y for y in range(100) if y % 2 == 0 if y % 5 == 0]
    print(num_list)
    # Output: [0, 10, 20, 30, 40, 50, 60, 70, 80, 90]

