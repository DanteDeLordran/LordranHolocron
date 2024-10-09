# Collections in Python

Start typing here...

## Reverse a collection

```Python
def reverse(collection):
    reversed = collection[::-1]
    return reversed
```

### append()

You can add an item to the end of a list using the append() method

### insert()

The insert method can add an element at any position in a list. The first argument is the position at which the element 
has to be added, and the second argument is the element to add.

```Python
example_list = [4, 5, 6, 7]
example_list.insert(2, 5.5)
print(example_list) # [4, 5, 5.5, 6, 7]
```

### pop()

The pop() method can be used to remove an element from a list. By default, it removes the last element of the list. 
You can pass an index as the argument to the method, and it will remove the element at the given index.

```Python
fruits_list = ["cherry", "lemon", "tomato", "apple", "orange"]
fruits_list.pop(2)
print(fruits_list) # ["cherry", "lemon", "apple", "orange"]
```