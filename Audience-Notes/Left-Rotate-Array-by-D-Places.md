Left Rotate Array by D Places

1. Problem Statement

Given an array of integers and an integer D, rotate the array to the left by D places.

Return the modified array.

---

2. Problem Explanation

In a left rotation:

* Elements move towards the left.
* Elements falling off from the beginning reappear at the end.

Example

Input:

arr = [1,2,3,4,5,6,7]

D = 3

Output:

[4,5,6,7,1,2,3]

Explanation:

The first 3 elements move to the end.

The remaining elements shift left.

---

3. Intuition (Brute Force)

Rotate the array by one place D times.

For each rotation:

* Store the first element.
* Shift all elements one position to the left.
* Place the stored element at the end.

Example

arr = [1,2,3,4,5]

D = 2

After 1st rotation:

[2,3,4,5,1]

After 2nd rotation:

[3,4,5,1,2]

Answer:

[3,4,5,1,2]

Complexity

Time Complexity : O(N × D)

Space Complexity : O(1)

---

4. Better Approach

Observation:

Instead of rotating one place D times,

store the first D elements in a temporary array.

Shift the remaining elements to the left.

Place the stored elements at the end.

Example

arr = [1,2,3,4,5,6,7]

D = 3

Store:

[1,2,3]

Shift:

[4,5,6,7]

Append stored elements:

[4,5,6,7,1,2,3]

Complexity

Time Complexity : O(N)

Space Complexity : O(D)

---

5. Optimal Approach

Pattern:

Array Reversal

Rotation by Reversal Algorithm

Observation:

D may be larger than N.

First calculate:

D = D % N

Then:

Step 1:

Reverse first D elements.

Step 2:

Reverse remaining elements.

Step 3:

Reverse entire array.

Example

arr = [1,2,3,4,5,6,7]

D = 3

---

Reverse first 3 elements

[3,2,1,4,5,6,7]

---

Reverse remaining elements

[3,2,1,7,6,5,4]

---

Reverse entire array

[4,5,6,7,1,2,3]

Answer:

[4,5,6,7,1,2,3]

Complexity

Time Complexity : O(N)

Space Complexity : O(1)

---

6. Common Mistakes

Mistake 1

Forgetting:

D = D % N

Example:

N = 7

D = 10

Actual rotation:

10 % 7 = 3

---

Mistake 2

Reversing the sections in the wrong order.

Correct Order:

1. First D Elements

2. Remaining Elements

3. Entire Array

---

Mistake 3

Incorrect reverse boundaries.

---

Mistake 4

Using brute force even after identifying the reversal pattern.

---

7. Code

Brute Force Approach

```java
public void leftRotate(int[] arr, int d) {

    int n = arr.length;

    for(int k = 0; k < d; k++) {

        int first = arr[0];

        for(int i = 0; i < n - 1; i++) {

            arr[i] = arr[i + 1];
        }

        arr[n - 1] = first;
    }
}
```

---

Better Approach

```java
public void leftRotate(int[] arr, int d) {

    int n = arr.length;

    d = d % n;

    int[] temp = new int[d];

    for(int i = 0; i < d; i++) {

        temp[i] = arr[i];
    }

    for(int i = d; i < n; i++) {

        arr[i - d] = arr[i];
    }

    for(int i = 0; i < d; i++) {

        arr[n - d + i] = temp[i];
    }
}
```

---

Optimal Approach

```java
public void leftRotate(int[] arr, int d) {

    int n = arr.length;

    d = d % n;

    reverse(arr, 0, d - 1);

    reverse(arr, d, n - 1);

    reverse(arr, 0, n - 1);
}

private void reverse(int[] arr, int left, int right) {

    while(left < right) {

        int temp = arr[left];
        arr[left] = arr[right];
        arr[right] = temp;

        left++;
        right--;
    }
}
```

---

8. Pattern Recognition

Pattern:

Array Reversal

Rotation by Reversal Algorithm

Observation:

Array rotation can be converted into a sequence of reversals.

Trigger Words:

* Rotate Array
* Left Rotate
* Rotate by D Places
* In Place Rotation

Think:

Can I reduce D using:

D = D % N

Can I use the reversal algorithm?

---

9. Problem Link

LeetCode 189 - Rotate Array

https://leetcode.com/problems/rotate-array/

---

10. YouTube Link

YouTube Video:

(Paste your YouTube video link here)
