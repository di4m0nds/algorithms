# Advanced **Data Structures** And **Algorithms** 

- **Data Structures**:

    ➡ Data structures allow us to store and organize our data effectively. There exists a wide variety of data structures, and depending on the needs of our algorithm or project, we choose the one that best fits our problem. We can broadly classify these structures into two categories: **linear** and **non-linear**.
    * **Linear structures** are those where the data is arranged sequentially, one after the other. Examples: **Arrays**, **Strings**, **Linked Lists**, **Stacks**, **Queues**, and more.
    * On the other hand, **Non-linear structures** are not sequentially organized. They are better known for their hierarchical organization, where data elements are linked to each other through relationships. Examples: **Graphs** and **Trees**.

- **Algorithms**:

    ➡ Algorithms are a series of **step-by-step instructions** that enable us to solve problems efficiently. By connecting these steps with the appropriate data structures, we can achieve effective solutions to problems.

## Big O Notation

It is a metric/language that allow us to describe the amount of resources that we use when algorithm runs. Examples: if our interest is the time, describe how long take to run the algorithm using a certain quantity of data (input data). The **WROST case possible**. Ex: $O(F(n))$

| Big O Notation           | Representation    | Examples                          |
|--------------------------|-------------------|-----------------------------------|
| 🟢 **Constant**     | $O(1)$            | Accessing a specific element in an array |
| 🟢 **Logarithmic**  | $O(\log n)$       | Binary search in a sorted array   |
| 🟡 **Linear**       | $O(n)$            | Finding the maximum element in an unsorted array |
| 🟠 **Linearithmic** | $O(n \log n)$     | Merge sort, quicksort             |
| 🟠 **Quadratic**    | $O(n^2)$          | Bubble sort, selection sort       |
| 🟠 **Polynomial**   | $O(n^k)$          | Matrix multiplication, algorithms with nested loops   |
| 🔴 **Factorial**    | $O(n!)$           | Finding all permutations of a set                     |


### **Linear Complexity** → $O(n)$
  
> *Example*: $O(\cancel{1}) + O(n) + O(n) O(\cancel{2n}) = \mathbf{O(n)}$

<details>

```python
def linear_complexity(arr):
    plus = 0                    # O(1) 🟢
    multiply = 1

    for n in range(len(arr)):   # O(n) 🟡
        plus += n

    for n in range(len(arr)):   # O(n) 🟡
        multiply *= n

    return plus, multiply
```
</details>
  
> *Example*: $O(\cancel{5}n) = \mathbf{O(n)}$

<details>

```python
def linear_complexity_2(arr):
    result = 0

    for i in range(len(arr)):   # O(n) 🟡
      for j in range(len(1, 5)):   # O(5) 🟢
        result += (i*j)

    return result
```
</details>

### **Logarithmic Complexity** → $O(\log n)$

<details>

```python
def binary_search(arr, target):
    pointer_left = 0
    pointer_right = len(arr) -1

    while pointer_left <= pointer_right:
        mid = (pointer_left+pointer_right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            pointer_left = mid + 1
        else arr[mid] < target:
            pointer_right = mid - 1

    return -1
```
</details>
<details>
    <summary>If the array is [1,3, 8, 14, 15,22, 22, 29, 28, 30,32, 38, 44, 47] and the element isn't in the list</summary>

    Iteration 1: run [1, 3, 8, 14,15, 22, 22, 23, 28,30,32,33,44,47]
    Iteration 2: run [1,3,8,14,15,22, 22]
    Iteration 3: run [1,3, 8, 14]
    Iteration 4: run [1,3]
    Iteration 5: run [1]
</details>

### **Linearithmic Complexity** → $O(n \log n)$

> *Example*: Merge Sort sorting algorithm

<details>

```python
def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr) // 2
        izquierdo = arr[:mid]
        derecho = arr[mid:]
        merge_sort(izquierdo)
        merge_sort(derecho)
        
        i = j = k = 0
        while i < len(izquierdo) and j < len(derecho):
            if izquierdo[i] < derecho[j]:
                arr[k] = izquierdo[i]
                i += 1
            else:
                arr[k] = derecho[j]
                j += 1
            k += 1
            
        while i < len(izquierdo):
            arr[k] = izquierdo[i]
            i += 1
            k += 1
            
        while j < len(derecho):
            arr[k] = derecho[j]
            j += 1
            k += 1
```
</details>

### **Quadratic Complexity** → $O(n^2)$
  
> *Example*: $O(n * n) = \mathbf{O(n^2)}$

<details>

```python
# 🟠 O(n^2)
def quadratic_complexity(matrix):
    for i in range(len(matrix)):        # O(n) 🟡
        for j in range(len(matrix[0])): # O(n) 🟡
            if matrix[i][j] != 0:
                print(matrix[i][j])

```
</details>

> *Example*: $\cancel{O(n \log n)} + O(n^2) + \cancel{O(n)} = \mathbf{O(n^2)}$. When dealing with large inputs, we choose the highest complexity present, which in this case is quadratic time.

<details>

```python
def three_sum(numeros: List[int]) -> List[List[int]]:
    if len(numeros) < 3:
        return []
    
    numeros.sort()          # O(n log n) 🟠
    resultado = set()
    
    for i in range(len(numeros) - 2):       # O(n) 🟡 ---|
        if numeros[i] <= 0:                             #|
            if i == 0 or numeros[i - 1] < numeros[i]:   #|--- O(n^2) 🟠
                mapaParejas = {}                        #|
                for num in numeros[i + 1:]: # O(n) 🟡 ---|
                    if num not in mapaParejas:
                        mapaParejas[-numeros[i] - num] = 1
                    else:
                        resultado.add((numeros[i], num, -numeros[i] - num))
    
    return [list(group) for group in resultado] # O(n) 🟡
```
</details>

