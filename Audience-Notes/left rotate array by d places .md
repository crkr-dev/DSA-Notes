Left Rotate Array by D Places

Problem Statement

Given an array arr[] of size n and an integer d, rotate the array to the left by d places.

Problem Explanation

In a left rotation, the first d elements move to the end of the array, and the remaining elements shift towards the left.

Example

Input:

arr = [1,2,3,4,5,6,7]
d = 2

Output:

[3,4,5,6,7,1,2]

Explanation:

First d elements:

[1,2]

Remaining elements:

[3,4,5,6,7]

After rotation:

[3,4,5,6,7,1,2]

Intuition (Brute Force)

The simplest way is to rotate the array by one position, d times.

Steps

Store the first element.
Shift all elements one position to the left.
Place the stored element at the end.
Repeat the above process d times.

Example

Array = [1,2,3,4,5]
d = 2

After 1 rotation:

[2,3,4,5,1]

After 2 rotations:

[3,4,5,1,2]

Complexity

Time Complexity : O(n*d)

Space Complexity : O(1)

Better Approach

Instead of rotating one position d times:

Store the first d elements in a temporary array.
Shift the remaining elements to the left.
Copy the temporary elements to the end.

Example

Array:

[1,2,3,4,5,6,7]

d = 2

temp = [1,2]

Shift remaining elements:

[3,4,5,6,7,6,7]

Copy temp elements at the end:

[3,4,5,6,7,1,2]

Complexity

Time Complexity : O(n)

Space Complexity : O(d)

Optimal Approach

Observation

Instead of shifting elements, we can use the Reversal Algorithm.

Example

Array = [1,2,3,4,5,6,7]

d = 2

Step 1

Reverse first d elements.

[2,1,3,4,5,6,7]

Step 2

Reverse remaining elements.

[2,1,7,6,5,4,3]

Step 3

Reverse the entire array.

[3,4,5,6,7,1,2]

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

Common Mistakes

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

reverse(arr, 0, d - 1);

reverse(arr, d, n - 1);

reverse(arr, 0, n - 1);

Mistake 3

Confusing Left Rotation and Right Rotation.

Always verify the expected output using a small example.

Code

Brute Force Approach

public static void leftRotate(int[] arr, int d) {

int n = arr.length;

for (int k = 0; k < d; k++) {

    int first = arr[0];

    for (int i = 1; i < n; i++) {
        arr[i - 1] = arr[i];
    }

    arr[n - 1] = first;
}

}

Better Approach

public static void leftRotate(int[] arr, int d) {

int n = arr.length;

d = d % n;

int[] temp = new int[d];

for (int i = 0; i < d; i++) {
    temp[i] = arr[i];
}

for (int i = d; i < n; i++) {
    arr[i - d] = arr[i];
}

for (int i = 0; i < d; i++) {
    arr[n - d + i] = temp[i];
}

}

Optimal Approach

public static void leftRotate(int[] arr, int d) {

int n = arr.length;

d = d % n;

reverse(arr, 0, d - 1);

reverse(arr, d, n - 1);

reverse(arr, 0, n - 1);

}

private static void reverse(int[] arr, int left, int right) {

while (left < right) {

    int temp = arr[left];
    arr[left] = arr[right];
    arr[right] = temp;

    left++;
    right--;
}

}

Problem Link

LeetCode 189 - Rotate Array

https://leetcode.com/problems/rotate-array/

YouTube Link

YouTube Video:

(Paste your YouTube video link here)
