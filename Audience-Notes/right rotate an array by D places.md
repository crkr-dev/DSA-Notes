
Right Rotate Array by D Places

1. Problem Statement

Given an array arr[] of size n and an integer d, rotate the array to the right by d places.

---

2. Problem Explanation

In a right rotation, the last d elements move to the beginning of the array, and the remaining elements shift towards the right.

Example

Input:

arr = [1,2,3,4,5,6,7]
d = 2

Output:

[6,7,1,2,3,4,5]

Explanation:

Last d elements:

[6,7]

Remaining elements:

[1,2,3,4,5]

After rotation:

[6,7,1,2,3,4,5]

---

3. Intuition (Brute Force)

The simplest way is to rotate the array by one position to the right, d times.

Steps

1. Store the last element.
2. Shift all elements one position to the right.
3. Place the stored element at the beginning.
4. Repeat the process d times.

Example

Array = [1,2,3,4,5]
d = 2

After 1 rotation:

[5,1,2,3,4]

After 2 rotations:

[4,5,1,2,3]

Complexity

Time Complexity  : O(n*d)

Space Complexity : O(1)

---

4. Better Approach

Instead of rotating one position d times:

1. Store the last d elements in a temporary array.
2. Shift the remaining elements to the right.
3. Copy the temporary elements to the beginning.

Example

Array:

[1,2,3,4,5,6,7]

d = 2

temp = [6,7]

Shift remaining elements right:

[1,2,1,2,3,4,5]

Copy temp at the beginning:

[6,7,1,2,3,4,5]

Complexity

Time Complexity  : O(n)

Space Complexity : O(d)

---

5. Optimal Approach

Observation

Instead of shifting elements, we can use the Reversal Algorithm.

Example

Array = [1,2,3,4,5,6,7]

d = 2

Step 1

Reverse the entire array.

[7,6,5,4,3,2,1]

Step 2

Reverse the first d elements.

[6,7,5,4,3,2,1]

Step 3

Reverse the remaining elements.

[6,7,1,2,3,4,5]

Complexity

Time Complexity  : O(n)

Space Complexity : O(1)

---

6. Common Mistakes

Mistake 1

Forgetting:

d = d % n;

Example:

n = 5
d = 7

Actual rotation required:

7 % 5 = 2

Mistake 2

Using incorrect reverse boundaries.

Correct:

reverse(arr, 0, n - 1);

reverse(arr, 0, d - 1);

reverse(arr, d, n - 1);

Mistake 3

Confusing Left Rotation and Right Rotation.

Remember:

Left Rotation:

Reverse Left Part

Reverse Right Part

Reverse Entire Array

Right Rotation:

Reverse Entire Array

Reverse First d Elements

Reverse Remaining Elements

---

7. Code

Brute Force Approach

public static void rightRotate(int[] arr, int d) {

```
int n = arr.length;

for (int k = 0; k < d; k++) {

    int last = arr[n - 1];

    for (int i = n - 1; i > 0; i--) {
        arr[i] = arr[i - 1];
    }

    arr[0] = last;
}
```

}

Better Approach

public static void rightRotate(int[] arr, int d) {

```
int n = arr.length;

d = d % n;

int[] temp = new int[d];

for (int i = 0; i < d; i++) {
    temp[i] = arr[n - d + i];
}

for (int i = n - d - 1; i >= 0; i--) {
    arr[i + d] = arr[i];
}

for (int i = 0; i < d; i++) {
    arr[i] = temp[i];
}
```

}

Optimal Approach

public static void rightRotate(int[] arr, int d) {

```
int n = arr.length;

d = d % n;

reverse(arr, 0, n - 1);

reverse(arr, 0, d - 1);

reverse(arr, d, n - 1);
```

}

private static void reverse(int[] arr, int left, int right) {

```
while (left < right) {

    int temp = arr[left];
    arr[left] = arr[right];
    arr[right] = temp;

    left++;
    right--;
}
```

}

---

8. Problem Link

LeetCode 189 - Rotate Array

https://leetcode.com/problems/rotate-array/

---

9. YouTube Link

YouTube Video:

(Paste your YouTube video link here)
