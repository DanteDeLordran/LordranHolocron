# Loops in Python

In Python, loops are used to repeatedly execute a block of code while a condition is met. There are two primary types 
of loops in Python: for loops and while loops. Both loops serve different purposes but can sometimes be interchangeable 
based on the use case.


## for

The for loop is used to iterate over items of a collection (such as lists, tuples, or strings) or any other iterable 
object.

```Python
numbers = [1, 2, 3, 4, 5]
for number in numbers:
print(number)
```

### break

The break statement is used to exit the loop prematurely when a certain condition is met.

```Python
for i in range(10):
if i == 5:
break  # Exit loop when i equals 5
print(i)
```

### continue

The continue statement is used to skip the current iteration and move on to the next iteration.

```Python
for i in range(5):
if i == 2:
continue  # Skip the iteration when i equals 2
print(i)
```

### else

An optional else clause can be added to both for and while loops. The else block executes if the loop completes 
normally (i.e., without encountering a break statement).

```Python
for i in range(3):
print(i)
else:
print("Loop completed without a break.")
```

### enumerate

When iterating over a sequence, you might want to keep track of both the index and the value. The enumerate() 
function makes this easy.

```
fruits = ['apple', 'banana', 'cherry']
for index, fruit in enumerate(fruits):
print(f'{index}: {fruit}')
```

### zip

The zip() function allows you to loop through two (or more) iterables at the same time.

```Python
names = ['Alice', 'Bob', 'Charlie']
ages = [25, 30, 35]

for name, age in zip(names, ages):
print(f'{name} is {age} years old.')
```

### reversed

You can loop through a sequence in reverse order using reversed().

```Python
numbers = [1, 2, 3, 4]
for num in reversed(numbers):
print(num)  # Output: 4, 3, 2, 1
```

## while

The while loop is used to execute a block of code repeatedly as long as the condition remains True. Be careful not to 
create an infinite loop!

```Python
count = 0
while count < 5:
print(count)
count += 1
```