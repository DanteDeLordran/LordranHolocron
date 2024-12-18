# Collections in Python

## List

### Reverse a collection

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

### filter()

The filter() function allows you to select items from an iterable, such as a list, based on the output of a function:

```Python
filter(my_function, my_list)
```

filter() takes a function as its first argument and an iterable as its second argument. It returns an iterator, which
is a special object that enables you to iterate over the elements of a collection, like a list.

### join()

The join method works by concatenating each element of a list into a string, separated by a designated string, known
as the separator.

```Python
result_string = ''.join(characters)
```

The example above joins together the elements of the characters list into a single string where each element is
concatenated together using an empty string as the separator.

The .extend() method, allows you to add elements from an iterable to the end of a list:

```Python
my_list = ['larch', 'birch']
tree_list = ['fir', 'redwood', 'pine']
my_list.extend(tree_list)
print(my_list) # Output: ['larch', 'birch', 'fir', 'redwood', 'pine']
```

## Tuple

## Dict

Dictionaries store data in the form of key-value pairs. A key is separated from the correspondent value by a colon. 
And each key-value pair is separated from the following pair by a comma:

```Python
my_dict = {
    'name': 'Michael',
    'occupation': 'Lumberjack'
}
```

To add a new key-value pair after declaring a dictionary, you can indicate the key in the same way you would access 
an existing key, and set the value of the new key by using the assignment operator:

```Python
my_dict = {
    'name': 'Michael',
    'occupation': 'Lumberjack'
}

my_dict['country'] = 'Canada'
```

If you want to be able to go through the key-value pairs, you can use the .items() method.

```Python
my_dict = {
    'name': 'Michael',
    'occupation': 'Lumberjack'
}

my_dict['country'] = 'Canada'
for i in copper: # Print keys
    print(i)
for i in copper.values(): # Print values
    print(i)
for i in copper.items(): # Print entire dict
    print(i)
```

You can remove a key-value pair from a dictionary by using the del keyword:

```Python
my_dict = {
'name': 'Michael',
'occupation': 'Lumberjack'
}

del my_dict['occupation']
```

### Dict example

```Python
my_graph = {
    'A': [('B', 5), ('C', 3), ('E', 11)],
    'B': [('A', 5), ('C', 1), ('F', 2)],
    'C': [('A', 3), ('B', 1), ('D', 1), ('E', 5)],
    'D': [('C',1 ), ('E', 9), ('F', 3)],
    'E': [('A', 11), ('C', 5), ('D', 9)],
    'F': [('B', 2), ('D', 3)]
}

def shortest_path(graph, start, target = ''):
    unvisited = list(graph)
    distances = {node: 0 if node == start else float('inf') for node in graph}
    paths = {node: [] for node in graph}
    paths[start].append(start)
    
    while unvisited:
        current = min(unvisited, key=distances.get)
        for node, distance in graph[current]:
            if distance + distances[current] < distances[node]:
                distances[node] = distance + distances[current]
                if paths[node] and paths[node][-1] == node:
                    paths[node] = paths[current][:]
                else:
                    paths[node].extend(paths[current])
                paths[node].append(node)
        unvisited.remove(current)
    
    targets_to_print = [target] if target else graph
    for node in targets_to_print:
        if node == start:
            continue
        print(f'\n{start}-{node} distance: {distances[node]}\nPath: {" -> ".join(paths[node])}')
    
    return distances, paths
    
shortest_path(my_graph, 'A', 'F')
```


## Set

