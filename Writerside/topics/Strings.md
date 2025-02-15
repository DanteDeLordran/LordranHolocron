# Strings in Python

Python strings are sequences of characters enclosed in single, double, or triple quotes. Strings in Python are immutable, 
meaning once they are created, they cannot be changed. You can access individual characters using indexing or manipulate 
strings with various built-in methods.

## Slicing

Extract a substring using a start and end index.

```python
text = "Python"
print(text[1:4])  # Output: yth
print(text[:3])   # Output: Pyt
print(text[3:])   # Output: hon
```

## Finding and Replacing

### find()

Returns the lowest index of the substring if found, otherwise returns -1.

```Python
text = "Hello, World!"
print(text.find('World'))  # Output: 7
print(text.find('Python')) # Output: -1
```

### index()

Same as find(), but raises a ValueError if the substring is not found.

```Python
text = "Hello, World!"
print(text.index('World'))  # Output: 7
# print(text.index('Python'))  # Raises ValueError
```

### replace()

Replaces occurrences of a substring with another substring.

```Python
text = "Hello, World!"
new_text = text.replace('World', 'Python')
print(new_text)  # Output: Hello, Python!
```

## String modification

### strip()

Removes leading and trailing whitespace.

```Python
text = "   Hello, World!   "
print(text.strip())  # Output: "Hello, World!"
```

### lstrip()

Removes leading whitespace.

```Python
text = "   Hello, World!"
print(text.lstrip())  # Output: "Hello, World!"
```

### rstrip()

Removes trailing whitespace.

```Python
text = "Hello, World!   "
print(text.rstrip())  # Output: "Hello, World!"
```

## String joining and splitting

### split()

Splits the string into a list based on the specified delimiter (default is whitespace).

```Python
text = "Hello, World!"
words = text.split(", ")
print(words)  # Output: ['Hello', 'World!']
```

### join()

Joins elements of a list into a string using a specified separator.

```Python
words = ['Hello', 'World!']
sentence = ", ".join(words)
print(sentence)  # Output: Hello, World!
```

## Examples

### Example using join()

```Python
def convert_to_snake_case(pascal_or_camel_cased_string):
    snake_cased_char_list = []
    for char in pascal_or_camel_cased_string:
        if char.isupper():
            converted_character = '_' + char.lower()
            snake_cased_char_list.append(converted_character)
        else:
            snake_cased_char_list.append(char)
    snake_cased_string = ''.join(snake_cased_char_list)
    clean_snake_cased_string = snake_cased_string.strip('_')

    return clean_snake_cased_string
```