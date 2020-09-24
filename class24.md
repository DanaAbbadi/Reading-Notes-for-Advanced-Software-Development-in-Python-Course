# Hash Tables

Hash tables are used to implement map and set data structures in most common programming languages. Python have builtin dictionaries and maps. A hash table is an unordered collection of key-value pairs, where each key is unique.

Hash Tables are used for:

* Hold unique values
* Dictionary
* Library


Basically, a hash code turns a key into an integer. It’s very important that hash codes are deterministic: their output is determined only by their input. Hash codes should never have randomness to them. The same key should always produce the same hash code.

**Creating a Hash**

A hashtable traditionally is created from an array. I always like the size 1024. this is important for index placement. After you have created your array of the appropriate size, do some sort of logic to turn that “key” into a numeric number value. Here is a possible suggestion:

1. Add or multiply all the ASCII values together.
2. Multiply it by a prime number such as 599.
3. Use modulo to get the remainder of the result, when divided by the total size of the array.
4. Insert into the array at that index.

### Hashing with chaining

The most common hash table implementation uses chaining with linked lists to resolve collisions. This combines the best properties of arrays and linked lists.

Hash table operations are performed in two steps:

1. A key is converted into an integer index by using a hash function.
2. This index decides the linked list where the key-value pair record belongs.

![img](https://yourbasic.org/algorithms/hash-table.png)

For example, let's create a data structure that can store up to 1000 records with random integer keys.

To distribute the data evenly, we use several short lists. All records with keys that end with 000 belong to one list, those with keys that end with 001 belong to another one, and so on. There is a total of 1000 such lists. This structure can be represented as an array of lists:

    var table = new LinkedList[1000]

where LinkedList denotes a linked list of key-value pairs.

Inserting a new record (key, value) is a two-step procedure:

1. we extract the three last digits of the key, hash = key % 1000,
2. and then insert the key and its value into the list located at table[hash].

        hash = key % 1000
        table[hash].AddFirst(key, value)

A lookup is implemented by

        value = table[key%1000].Find(key)

Since the keys are random, there will be roughly the same number of records in each list. Since there are 1000 lists and at most 1000 records, there will likely be very few records in the list table[ key%1000] and therefore the lookup operation will be fast.



