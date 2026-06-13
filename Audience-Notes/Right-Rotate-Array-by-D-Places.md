Right Rotate Array by D Places

1. Problem Statement

Given an array of integers and an integer D, rotate the array to the right by D places.

Return the modified array.

---

2. Problem Explanation

In a right rotation:

* Elements move towards the right.
* Elements that move beyond the last index reappear at the beginning.

Example

Input:

arr = [1,2,3,4,5,6,7]

D = 3

Output:

[5,6,7,1,2,3,4]

Explanation:

The last 3 elements move to the front.

The remaining elements shift right.

---

3. Intuition (Brute Force)

Rotate the array by one place D times.

For every rotation:

* Store the last element.
* Shift all elements one position to the right.
* Place the stored element at index 0.

Example

arr = [1,2,3,4,5]

D = 2

After 1st Rotation:

[5,1,2,3,4]

After 2nd Rotation:

[4,5,1,2,3]

Answer:

[4,5,1,2,3]

Complexity

Time Complexity : O(N × D)

Space Complexity : O(1)

---

4. Better Approach

Observation:

Instead of rotating one place D times,

store the last D elements in a temporary array.

Shift the remaining elements to the right.

Place the stored elements at the beginning.

Example

arr = [1,2,3,4,5,6,7]

D = 3

Store:

[5,6,7]

Shift remaining elements:

[1,2,3,4]

Place stored elements at front:

[5,6,7,1,2,3,4]

Complexity

Time Complexity : O(N)

Space Complexity : O(D)

---

5. Optimal Approach

Pattern:

Array Reversal

Rotation by Reversal Algorithm

Observation:

D may be greater than N.

First calculate:

D = D % N

Then:

Step 1:

Reverse the entire array.

Step 2:

Reverse the first D elements.

Step 3:

Reverse the remaining elements.

Example

arr = [1,2,3,4,5,6,7]

D = 3

---

Reverse entire array

[7,6,5,4,3,2,1]

---

Reverse first D elements

[5,6,7,4,3,2,1]

---

Reverse remaining elements

[5,6,7,1,2,3,4]

Answer:

[5,6,7,1,2,3,4]

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

Actual Rotation:

10 % 7 = 3

---

Mistake 2

Reversing sections in the wrong order.

Correct Order:

1. Entire Array

2. First D Elements

3. Remaining Elements

---

Mistake 3

Incorrect reverse boundaries.

---

Mistake 4

Using brute force after identifying the reversal pattern.

---

7. Code

Brute Force Approach

```java
public void rightRotate(int[] arr, int d) {

    int n = arr.length;

    for(int k = 0; k < d; k++) {

        int last = arr[n - 1];

        for(int i = n - 1; i > 0; i--) {

            arr[i] = arr[i - 1];
        }

        arr[0] = last;
    }
}
```

---

Better Approach

```java
public void rightRotate(int[] arr, int d) {

    int n = arr.length;

    d = d % n;

    int[] temp = new int[d];

    for(int i = 0; i < d; i++) {

        temp[i] = arr[n - d + i];
    }

    for(int i = n - d - 1; i >= 0; i--) {

        arr[i + d] = arr[i];
    }

    for(int i = 0; i < d; i++) {

        arr[i] = temp[i];
    }
}
```

---

Optimal Approach

```java
public void rightRotate(int[] arr, int d) {

    int n = arr.length;

    d = d % n;

    reverse(arr, 0, n - 1);

    reverse(arr, 0, d - 1);

    reverse(arr, d, n - 1);
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

Rotation can be achieved through a sequence of reversals.

Trigger Words:

* Rotate Array
* Right Rotate
* Rotate by D Places
* O(1) Space
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
