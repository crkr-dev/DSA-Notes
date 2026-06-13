Right Rotate Array by One Place

1. Problem Statement

Given an array of integers, rotate the array to the right by one position.

The last element should move to the first position.

Return the modified array.

---

2. Problem Explanation

In a right rotation by one place:

* The last element moves to the beginning.
* Every other element shifts one position to the right.

Example

Input:

arr = [1,2,3,4,5]

Output:

[5,1,2,3,4]

Explanation:

5 moves to the front.

All remaining elements shift right by one position.

---

3. Intuition (Brute Force)

Create a new array.

Place the last element at the first position.

Copy all remaining elements one position ahead.

Example

arr = [1,2,3,4,5]

Store:

5

Result:

[5,1,2,3,4]

Complexity

Time Complexity : O(N)

Space Complexity : O(N)

---

4. Better Approach

Observation:

We only need to save the last element.

All other elements can be shifted to the right inside the same array.

After shifting, place the stored element at index 0.

Complexity

Time Complexity : O(N)

Space Complexity : O(1)

---

5. Optimal Approach

Pattern:

Array Shifting

In-Place Modification

Observation:

Store the last element.

Shift every element one position to the right.

Place the stored element at the beginning.

Example

arr = [1,2,3,4,5]

Store:

temp = 5

---

Shift

arr[4] = arr[3]

arr[3] = arr[2]

arr[2] = arr[1]

arr[1] = arr[0]

Array becomes:

[1,1,2,3,4]

---

Place temp at index 0

[5,1,2,3,4]

Answer:

[5,1,2,3,4]

Complexity

Time Complexity : O(N)

Space Complexity : O(1)

---

6. Common Mistakes

Mistake 1

Overwriting the last element without storing it first.

---

Mistake 2

Shifting from left to right.

Always shift from right to left.

---

Mistake 3

Using incorrect loop boundaries.

---

Mistake 4

Forgetting to place the stored element at index 0.

---

7. Code

Brute Force Approach

```java
public int[] rightRotateByOne(int[] arr) {

    int n = arr.length;

    int[] result = new int[n];

    result[0] = arr[n - 1];

    for(int i = 0; i < n - 1; i++) {

        result[i + 1] = arr[i];
    }

    return result;
}
```

---

Optimal Approach

```java
public void rightRotateByOne(int[] arr) {

    int n = arr.length;

    int temp = arr[n - 1];

    for(int i = n - 1; i > 0; i--) {

        arr[i] = arr[i - 1];
    }

    arr[0] = temp;
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

Place the stored element on the opposite side.

Trigger Words:

* Right Rotate
* Rotate by One Place
* Shift Array
* Cyclic Rotation

Think:

Can I store the outgoing element?

Can I shift the remaining elements?

---

9. Problem Link

GeeksforGeeks - Cyclically Rotate an Array by One

https://www.geeksforgeeks.org/problems/cyclically-rotate-an-array-by-one2614/1

---

10. YouTube Link

YouTube Video:

(Paste your YouTube video link here)
