# Comprehensions

## List comprehension

In Python, a list comprehension is a construct that allows you to generate a new list by applying an expression to 
each item in an existing iterable and optionally filtering items with a condition. Apart from being briefer, 
list comprehensions often run faster.

A basic list comprehension consists of an expression followed by a for clause:

```Python
[expression for item in iterable if condition]
```

The above uses the variable i to iterate over iterable. Each element of the resulting list is obtained by evaluating 
the expression i * 2 at the current iteration.


### Filtering with a condition

```Python
even_numbers = [x for x in range(20) if x % 2 == 0]
print(even_numbers)  # Output: [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
```

### If else

```Python
numbers = [x if x % 2 == 0 else -x for x in range(10)]
print(numbers)  # Output: [0, -1, 2, -3, 4, -5, 6, -7, 8, -9]
```

### Nested list comprehension

```Python
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flat_list = [num for row in matrix for num in row]
print(flat_list)  # Output: [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### Nested list comprehension with multiple conditions

```Python
primes = [num for num in range(2, 51) if all(num % i != 0 for i in range(2, int(num ** 0.5) + 1))]
print(primes)  # Output: [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47]
```

## Dict comprehension

```Python
{key: val for key in dict}
```