# Python

Python is not my favorite language, in fact I kinda dislike it and like it at the same time, but is good for ML, 
and I do like ML

## Interesting Python behaviour

1. Mutability 

    Immutable: strings, tuples, integers, booleans

    Mutable: list, dictionaries

    So the way you want to increment the value of an integer is by
    
    ```Python
    a += 1
    ```
    This happens because this way Python is actually creating an entire new integer and reassigning its value to the
    variable

    The same happens to string, you actually need to create a new entire string in order to modify the existing one
    ```Python
    a = 'Im a string'
    a.strip() # This wont work
    a = a.strip() # This is the way
    ```

2. The ``` is ``` and the ``` == ``` operators
    
    When doing comparisons in Python we got the ``` is ``` and the ``` == ``` operators, but each has a different behaviour

    ```Python
    # Using '=='
    a = [1, 2, 3]
    b = [1, 2, 3]
    
    print(a == b) # True, because the values are the same
    print(a is b) # False, because they are different objects in memory
    c = a # c now refers to the same object as a
    print(a is c) # True, because c and a refer to the same object in memory
    ```
   
    So use ``` is ``` when you need to check if two variables refer to the same object.

    Use ``` == ``` when you want to check if two variables have equal values, regardless of whether they are stored in different memory locations.

3. The ```is not ``` and the ``` != ``` operators

    Use ``` != ``` when you want to compare the values of two objects to see if they are different.

    Use ```is not ``` when you want to check if two variables are not the same object.

    Use ``` not ``` when you need to reverse the boolean value of an expression.

In Python, the is keyword checks for object identity. It's used to determine if two variables point to the same 
object in memory. In contrast to is, the equality operator (==) determines if the values of two objects are the same, 
regardless of whether they are the same object in memory.