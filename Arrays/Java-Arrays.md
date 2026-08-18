# Java Arrays

## 1. What is an Array?

An array is a collection of elements of the **same data type** stored in a fixed-size structure.

An array allows us to store multiple values in a single variable instead of declaring separate variables.

Example:

```java
int[] numbers = {10, 20, 30, 40, 50};
```

Here:

* `int[]` → integer array
* `numbers` → array variable
* `{10, 20, 30, 40, 50}` → array elements
* Array index starts from **0**

```text
Index:    0   1   2   3   4
Value:   10  20  30  40  50
```

---

# 2. Declaring an Array

```java
int[] numbers;
```

Another valid syntax:

```java
int numbers[];
```

The preferred approach is:

```java
int[] numbers;
```

---

# 3. Creating an Array

```java
int[] numbers = new int[5];
```

This creates an integer array that can store **5 elements**.

Default values:

```text
int     → 0
double  → 0.0
boolean → false
char    → '\u0000'
Object  → null
```

Example:

```java
int[] numbers = new int[5];

System.out.println(numbers[0]);
```

Output:

```text
0
```

---

# 4. Initializing an Array

```java
int[] numbers = {10, 20, 30, 40, 50};
```

We can access elements using their index.

```java
System.out.println(numbers[0]);
System.out.println(numbers[2]);
System.out.println(numbers[4]);
```

Output:

```text
10
30
50
```

---

# 5. Array Index

Array indexes always start from **0**.

For:

```java
int[] numbers = {10, 20, 30, 40, 50};
```

The indexes are:

```text
0 → 10
1 → 20
2 → 30
3 → 40
4 → 50
```

The last index is:

```java
numbers.length - 1
```

---

# 6. Array Length

The `length` property returns the number of elements in an array.

```java
int[] numbers = {10, 20, 30, 40, 50};

System.out.println(numbers.length);
```

Output:

```text
5
```

Important:

For arrays:

```java
numbers.length
```

For Strings:

```java
name.length()
```

For collections:

```java
list.size()
```

---

# 7. Accessing Array Elements

```java
int[] numbers = {10, 20, 30, 40, 50};

System.out.println(numbers[0]);
System.out.println(numbers[3]);
```

Output:

```text
10
40
```

---

# 8. Updating Array Elements

Array elements can be modified using their index.

```java
int[] numbers = {10, 20, 30};

numbers[1] = 100;

System.out.println(numbers[1]);
```

Output:

```text
100
```

The array becomes:

```text
10  100  30
```

---

# 9. Loop Through an Array

## Using for loop

```java
int[] numbers = {10, 20, 30, 40, 50};

for (int i = 0; i < numbers.length; i++) {

    System.out.println(numbers[i]);

}
```

---

# 10. Enhanced for Loop

The enhanced `for` loop is commonly used when we only need the values.

```java
int[] numbers = {10, 20, 30, 40, 50};

for (int number : numbers) {

    System.out.println(number);

}
```

Difference:

```text
Normal for loop
→ Gives index + value

Enhanced for loop
→ Gives value directly
```

---

# 11. Find Sum of Array Elements

```java
int[] numbers = {10, 20, 30, 40, 50};

int sum = 0;

for (int number : numbers) {

    sum = sum + number;

}

System.out.println("Sum = " + sum);
```

Output:

```text
Sum = 150
```

---

# 12. Find Average

```java
int[] numbers = {10, 20, 30, 40, 50};

int sum = 0;

for (int number : numbers) {

    sum += number;

}

double average = (double) sum / numbers.length;

System.out.println("Average = " + average);
```

Output:

```text
Average = 30.0
```

---

# 13. Find Maximum Number

```java
int[] numbers = {10, 50, 20, 80, 30};

int max = numbers[0];

for (int number : numbers) {

    if (number > max) {

        max = number;

    }

}

System.out.println("Maximum = " + max);
```

Output:

```text
Maximum = 80
```

---

# 14. Find Minimum Number

```java
int[] numbers = {10, 50, 20, 80, 30};

int min = numbers[0];

for (int number : numbers) {

    if (number < min) {

        min = number;

    }

}

System.out.println("Minimum = " + min);
```

Output:

```text
Minimum = 10
```

---

# 15. Count Even Numbers

```java
int[] numbers = {10, 21, 32, 43, 54, 65};

int count = 0;

for (int number : numbers) {

    if (number % 2 == 0) {

        count++;

    }

}

System.out.println("Even count = " + count);
```

Output:

```text
Even count = 3
```

---

# 16. Count Odd Numbers

```java
int[] numbers = {10, 21, 32, 43, 54, 65};

int count = 0;

for (int number : numbers) {

    if (number % 2 != 0) {

        count++;

    }

}

System.out.println("Odd count = " + count);
```

---

# 17. Reverse an Array

```java
int[] numbers = {10, 20, 30, 40, 50};

for (int i = numbers.length - 1; i >= 0; i--) {

    System.out.println(numbers[i]);

}
```

Output:

```text
50
40
30
20
10
```

---

# 18. Search an Element

```java
int[] numbers = {10, 20, 30, 40, 50};

int search = 30;

boolean found = false;

for (int number : numbers) {

    if (number == search) {

        found = true;
        break;

    }

}

if (found) {

    System.out.println("Number found");

} else {

    System.out.println("Number not found");

}
```

---

# 19. Find Duplicate Numbers

```java
int[] numbers = {10, 20, 30, 20, 40, 10, 50};

for (int i = 0; i < numbers.length; i++) {

    for (int j = i + 1; j < numbers.length; j++) {

        if (numbers[i] == numbers[j]) {

            System.out.println("Duplicate = " + numbers[i]);

        }

    }

}
```

Output:

```text
Duplicate = 10
Duplicate = 20
```

---

# 20. Find Duplicate Numbers with Indexes

```java
int[] numbers = {10, 20, 30, 20, 40, 10, 50};

for (int i = 0; i < numbers.length; i++) {

    for (int j = i + 1; j < numbers.length; j++) {

        if (numbers[i] == numbers[j]) {

            System.out.println(
                numbers[i] +
                " found at indexes " +
                i + " and " + j
            );

        }

    }

}
```

Output:

```text
20 found at indexes 1 and 3
10 found at indexes 0 and 5
```

---

# 21. Sort an Array

Java provides `Arrays.sort()`.

```java
import java.util.Arrays;

int[] numbers = {50, 20, 40, 10, 30};

Arrays.sort(numbers);

System.out.println(Arrays.toString(numbers));
```

Output:

```text
[10, 20, 30, 40, 50]
```

---

# 22. Copy an Array

Using `Arrays.copyOf()`:

```java
import java.util.Arrays;

int[] numbers = {10, 20, 30};

int[] copy = Arrays.copyOf(numbers, numbers.length);

System.out.println(Arrays.toString(copy));
```

---

# 23. Compare Two Arrays

Do not use `==` to compare array contents.

Use:

```java
Arrays.equals()
```

Example:

```java
import java.util.Arrays;

int[] a = {10, 20, 30};
int[] b = {10, 20, 30};

System.out.println(Arrays.equals(a, b));
```

Output:

```text
true
```

---

# 24. Convert Array to String

Use:

```java
Arrays.toString()
```

Example:

```java
int[] numbers = {10, 20, 30};

System.out.println(Arrays.toString(numbers));
```

Output:

```text
[10, 20, 30]
```

---

# 25. Two-Dimensional Array

A two-dimensional array can be thought of as rows and columns.

```java
int[][] numbers = {
    {10, 20, 30},
    {40, 50, 60},
    {70, 80, 90}
};
```

Access:

```java
System.out.println(numbers[0][0]);
System.out.println(numbers[1][2]);
```

Output:

```text
10
60
```

---

# 26. Loop Through Two-Dimensional Array

```java
int[][] numbers = {
    {10, 20, 30},
    {40, 50, 60},
    {70, 80, 90}
};

for (int i = 0; i < numbers.length; i++) {

    for (int j = 0; j < numbers[i].length; j++) {

        System.out.print(numbers[i][j] + " ");

    }

    System.out.println();
}
```

Output:

```text
10 20 30
40 50 60
70 80 90
```

---

# 27. ArrayIndexOutOfBoundsException

This exception occurs when trying to access an index that doesn't exist.

```java
int[] numbers = {10, 20, 30};

System.out.println(numbers[5]);
```

Valid indexes are:

```text
0
1
2
```

Therefore, index `5` causes:

```text
ArrayIndexOutOfBoundsException
```

---

# 28. Array vs ArrayList

| Array                        | ArrayList                     |
| ---------------------------- | ----------------------------- |
| Fixed size                   | Dynamic size                  |
| Can store primitives         | Stores objects/wrapper types  |
| `length`                     | `size()`                      |
| Faster for simple fixed data | More flexible                 |
| Part of Java language        | Part of Collections Framework |

Example:

```java
int[] numbers = new int[5];
```

ArrayList:

```java
ArrayList<Integer> numbers = new ArrayList<>();
```

---

# 29. Important Array Methods

The `Arrays` utility class provides many useful methods.

```java
Arrays.sort()
Arrays.equals()
Arrays.toString()
Arrays.copyOf()
Arrays.fill()
Arrays.binarySearch()
Arrays.compare()
```

Example:

```java
int[] numbers = {10, 20, 30, 40, 50};

int index = Arrays.binarySearch(numbers, 30);

System.out.println(index);
```

Output:

```text
2
```

`binarySearch()` should normally be used on a **sorted array**.

---

# 30. Common Array Interview Questions

Practice these problems:

1. Find the largest number in an array.
2. Find the smallest number in an array.
3. Find the second-largest number.
4. Find the second-smallest number.
5. Reverse an array.
6. Find duplicate numbers.
7. Find duplicate numbers with indexes.
8. Remove duplicate numbers.
9. Count duplicate numbers.
10. Find the frequency of each number.
11. Find even numbers.
12. Find odd numbers.
13. Count even and odd numbers.
14. Find the sum of array elements.
15. Find the average.
16. Find a missing number.
17. Find common elements between two arrays.
18. Merge two arrays.
19. Sort an array without using `Arrays.sort()`.
20. Find the largest and smallest number in one pass.

---

# 31. Important Interview Points

### Array index

```text
Starts at 0
```

### Last index

```java
array.length - 1
```

### Array length

```java
array.length
```

### String length

```java
string.length()
```

### ArrayList size

```java
arrayList.size()
```

### Array sorting

```java
Arrays.sort(array);
```

### Array comparison

```java
Arrays.equals(array1, array2);
```

### Array printing

```java
Arrays.toString(array);
```

---

# 32. Quick Revision

```text
Array
 ↓
Fixed size
 ↓
Same data type
 ↓
Index starts at 0
 ↓
Last index = length - 1
```

Important operations:

```text
Create
Access
Update
Traverse
Search
Sort
Reverse
Copy
Compare
Find duplicates
Find min/max
Find sum/average
```

Important exception:

```text
ArrayIndexOutOfBoundsException
```

Important utility class:

```java
java.util.Arrays
```

---

# 33. Interview Example

### Question

Find the second-largest number in:

```text
10, 50, 20, 80, 30
```

Expected result:

```text
50
```

One possible approach:

```java
int[] numbers = {10, 50, 20, 80, 30};

int largest = Integer.MIN_VALUE;
int secondLargest = Integer.MIN_VALUE;

for (int number : numbers) {

    if (number > largest) {

        secondLargest = largest;
        largest = number;

    } else if (number > secondLargest && number != largest) {

        secondLargest = number;

    }
}

System.out.println("Largest = " + largest);
System.out.println("Second Largest = " + secondLargest);
```

Output:

```text
Largest = 80
Second Largest = 50
```

---

# 34. Key Takeaway

For Java interviews, understand arrays beyond basic declaration and traversal. Be comfortable solving problems involving **searching, sorting, duplicates, frequency, min/max, reversing, missing numbers, and comparing multiple arrays**.

Arrays are also important because they provide the foundation for understanding Java Collections such as `ArrayList`, `HashSet`, and `HashMap`.
