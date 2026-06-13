Left Rotate Array by One Place

1. Problem Statement

Given an array of integers, rotate the array to the left by one position.

The first element should move to the last position.

Return the modified array.

---

2. Problem Explanation

In a left rotation by one place:

* The first element moves to the last position.
* Every other element shifts one position to the left.

Example

Input:

arr = [1,2,3,4,5]

Output:

[2,3,4,5,1]

Explanation:

1 moves to the end.

All remaining elements shift left by one position.

---

3. Intuition (Brute Force)

Create a new array.

Store elements from index 1 onwards.

Place the first element at the last position.

Example

arr = [1,2,3,4,5]

Store:

[2,3,4,5]

Append first element:

[2,3,4,5,1]

Complexity

Time Complexity : O(n)

Space Complexity : O(n)

---

4. Better Approach

Observation:

We only need to save the first element.

All other elements can be shifted left inside the same array.

After shifting, place the saved element at the last position.

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

---

5. Optimal Approach

Pattern:

Array Shifting

In-Place Modification

Observation:

Store the first element.

Shift every element one step to the left.

Place the stored element at the last index.

Example

arr = [1,2,3,4,5]

Store:

temp = 1

---

Shift

arr[0] = 2

arr[1] = 3

arr[2] = 4

arr[3] = 5

Array becomes:

[2,3,4,5,5]

---

Place temp at last index

[2,3,4,5,1]

Answer:

[2,3,4,5,1]

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

---

6. Common Mistakes

Mistake 1

Overwriting the first element without storing it.

---

Mistake 2

Using extra arrays when an in-place solution is possible.

---

Mistake 3

Incorrect loop boundaries while shifting.

---

Mistake 4

Forgetting to place the first element at the last position.

---

7. Code

Brute Force Approach

```java
public int[] leftRotateByOne(int[] arr) {

    int n = arr.length;

    int[] result = new int[n];

    for(int i = 1; i < n; i++) {

        result[i - 1] = arr[i];
    }

    result[n - 1] = arr[0];

    return result;
}
```

---

Optimal Approach

```java
public void leftRotateByOne(int[] arr) {

    int n = arr.length;

    int temp = arr[0];

    for(int i = 1; i < n; i++) {

        arr[i - 1] = arr[i];
    }

    arr[n - 1] = temp;
}
```

---

8. Pattern Recognition

Pattern:

Array Shifting

In-Place Modification

Observation:

One element leaves the array from one side.

Store it temporarily.

Shift remaining elements.

Place the stored element at the opposite side.

Trigger Words:

* Left Rotate
* Shift Array
* Rotate by One
* In Place Rotation

Think:

Can I store the outgoing element?

Can I shift the remaining elements?

---

9. Problem Link

GeeksforGeeks - Rotate Array by One

https://www.geeksforgeeks.org/problems/cyclically-rotate-an-array-by-one2614/1

Note:

This GFG problem is a right rotation by one place.

For left rotation by one place, the logic is similar but in the opposite direction.

---

10. YouTube Link

YouTube Video:

(Paste your YouTube video link here)
