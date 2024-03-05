# Arrays & Strings

- **Arrays**:

  ➡ It's a lineal collection of data values, which can be accessed using numbered indices starting at 0. Each programming language may have data structures implemented differently, so it is important to check to understand the complexity of these structures.
  
  * **Dynamic Array**: this implementation establishes an array with twice the memory needed to store data. Adding values is a constant time operation, when it fills it makes a copy of the array and establishes double the memory.

      > *(ex: JS and PYTHON have dynamic arrays)*
  
  * **Static Array**: this implementation allocates a fixed memory size to store the values. Thus, to add values it's necessary to copy the array and establish a new memory size, considering the extra space needed for the new value. This is a linear time operation $O(n)$ .

  ➡ The following describes the standard operations of an array and their corresponding time complexities:

    - Accessing a value at a specific index: $O(1)$
    - Updating a value at a given index: $O(1)$
    - Inserting a value
        - $O(n)$ for a dynamic array
        - $O(1)$ for a static array
    - Removing a value at the beginning: $O(n)$
    - Removing a value in the middle: $O(n)$
    - Removing a value at the end: $O(1)$
    - Copying the array: $O(n)$

- **Strings**:

  ➡ Strings aren't exactly a data structure; they are arrays where each element represents a character. These characters are stored in memory as a list of whole numbers. Each character in a string is allocated a unique whole number based on a character encoding standard such as ASCII.
  
  ➡ The behavior of strings is quite similar to that of normal arrays, with the difference that in most programming languages (except C++), strings are immutable. This means that once a string is created, it cannot be modified. As a result, simple operations such as adding new characters to a string can be more costly than one might expect.

```python
string = "This is a string"
newString = ""

for char in string:
    newString += char
```

  > Example: Although creating a new string might itself be an $O(n)$ operation (depending on the implementation), performing it within the loop leads to the overall complexity becoming $O(n * n)$ which simplifies to $O(n^2)$ .

