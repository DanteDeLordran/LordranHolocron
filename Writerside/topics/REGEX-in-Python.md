# REGEX in Python

A regular expression, or regex, is a pattern used to match a specific combination of characters inside a string. It is 
a valid alternative to if/else conditional statements when you need to match or find patterns inside a string for 
validation purposes, character replacement, and others.

The compile() function from the re module compiles the string passed as the argument into a regular expression 
object that can be used by other re methods.

The search() function from the re module analyzes the string passed as the argument looking for the first place where 
the regex pattern matches the string.

findall()
It's similar to search, but it returns a list with all the occurrences of the matched pattern.

A character class is indicated by square brackets and matches one character among those specified between the brackets. 
For example, ma[dnt] matches either mad, man, or mat.

Character classes also allow you to indicate a range of characters to match. You need to specify the starting and the 
ending characters separated by a hyphen, -. Characters follow the Unicode order.

The caret, ^, placed at the beginning of the character class, matches all the characters except those specified in 
the class.

In a character class, you can combine multiple ranges by writing one range after another inside the square brackets 
(without any additional characters). For example: [a-d3-6] is the combination of [a-d] and [3-6].