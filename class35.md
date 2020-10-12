# Pythonisms

## Dunder Methods

Dunder or magic methods in Python are the methods having two prefix and suffix underscores in the method name. Dunder here means “Double Under (Underscores)”. These are commonly used for operator overloading.

Let’s look at various “dunder” methods to have the better understanding of various features Python provides.

#### Object Initialization: __init__

"__ init__" is a reseved method in python classes. It is known as a constructor in object oriented concepts. This method is called when an object is created from the class and it allow the class to initialize the attributes of a class.

Example:

    class Car(object):
 

        def __init__(self, model, color, company, speed_limit):
            self.color = color
            self.company = company
            self.speed_limit = speed_limit
            self.model = model


#### Object Representation: __str__, __repr__

**__str __** This method returns the string representation of the object. This method is called when print() or str() function is invoked on an object.

This method must return the String object. If we don’t implement __str __ () function for a class, then built-in object implementation is used that actually calls __repr __() function.

Python **__repr __** function returns the object representation. It could be any valid python expression such as tuple, dictionary, string etc.

This method is called when repr() function is invoked on the object, in that case, __repr __() function must return a String otherwise error will be thrown.

Example:

    class Person:
        
        def __init__(self, personName, personAge):
            self.name = personName
            self.age = personAge

        def __repr__(self):
            return {'name':self.name, 'age':self.age}

        def __str__(self):
            return 'Person(name='+self.name+', age='+str(self.age)+ ')'


#### Iteration: __len__, __getitem__, __reversed__

The built-in function len() calls the magic method __len __(). len () is the public interface you use to get the length of an object. The __len __ method is the implementation that an object that supports the concept of length is expected to implement. You normally shouldn't call dunder methods directly, although there are cases where it's required.

And this is a repeating pattern in Python:

    len() and __len__()
    iter() and __iter__()
    next() and __next__()
    format() and __format__()
    bool() and __bool__()
    hash() and __hash__()
    repr() and __repr__()
    str() and __str__()



## Python Iterators

Iterators are objects that can be iterated upon. Iterators are everywhere in Python. They are elegantly implemented within for loops, comprehensions, generators etc. but are hidden in plain sight.

Iterator in Python is simply an object that can be iterated upon. An object which will return data, one element at a time.

Technically speaking, a Python iterator object must implement two special methods, __iter__() and __next__(), collectively called the iterator protocol.

An object is called iterable if we can get an iterator from it. Most built-in containers in Python like: list, tuple, string etc. are iterables.

The iter() function (which in turn calls the __iter__() method) returns an iterator from them.

**Iterating Through an Iterator**

We use the next() function to manually iterate through all the items of an iterator. When we reach the end and there is no more data to be returned, it will raise the StopIteration Exception. 

```python
# define a list
my_list = [4, 7, 0, 3]

# get an iterator using iter()
my_iter = iter(my_list)

# iterate through it using next()

# Output: 4
print(next(my_iter))
```

## Python Generators

generator functions are a special kind of function that return a lazy iterator. These are objects that you can loop over like a list. However, unlike lists, lazy iterators do not store their contents in memory. For an overview of iterators in Python, take a look at Python “for” Loops (Definite Iteration).

### *Example:* Reading Large Files

A common use case of generators is to work with data streams or large files, like CSV files. These text files separate data into columns by using commas. This format is a common way to share data. Now, what if you want to count the number of rows in a CSV file? The code block below shows one way of counting those rows:

```python
csv_gen = csv_reader("some_csv.txt")
row_count = 0

for row in csv_gen:
    row_count += 1

print(f"Row count is {row_count}")
```

Looking at this example, you might expect csv_gen to be a list. To populate this list, csv_reader() opens a file and loads its contents into csv_gen. Then, the program iterates over the list and increments row_count for each row.

This is a reasonable explanation, but would this design still work if the file is very large? What if the file is larger than the memory you have available? To answer this question, let’s assume that csv_reader() just opens the file and reads it into an array:

```python
def csv_reader(file_name):
    file = open(file_name)
    result = file.read().split("\n")
    return result

```

This function opens a given file and uses file.read() along with .split() to add each line as a separate element to a list. If you were to use this version of csv_reader() in the row counting code block you saw further up, then you’d get the following output:

```python
Traceback (most recent call last):
  File "ex1_naive.py", line 22, in <module>
    main()
  File "ex1_naive.py", line 13, in main
    csv_gen = csv_reader("file.txt")
  File "ex1_naive.py", line 6, in csv_reader
    result = file.read().split("\n")
```

In this case, open() returns a generator object that you can lazily iterate through line by line.
