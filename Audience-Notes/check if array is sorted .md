Check if Array is Sorted

1. Problem Statement

Given an array arr[] of size n, check whether the array is sorted in non-decreasing order.

Return true if the array is sorted, otherwise return false.

---

2. Problem Explanation

An array is said to be sorted if every element is greater than or equal to its previous element.

Example 1

Input:

arr = [1,2,3,4,5]

Output:

true

Explanation:

Every element is greater than or equal to its previous element.

---

Example 2

Input:

arr = [1,3,2,4,5]

Output:

false

Explanation:

2 is smaller than 3.

So the array is not sorted.

---

3. Intuition (Brute Force)

To determine whether an array is sorted, we need to check every element with its previous element.

If we find even one element that is smaller than its previous element, the array is not sorted.

Otherwise, the array is sorted.

Steps

1. Start from index 1.
2. Compare the current element with the previous element.
3. If current element is smaller, return false.
4. If traversal completes, return true.

Example

arr = [1,2,3,4,5]

2 >= 1 ✔

3 >= 2 ✔

4 >= 3 ✔

5 >= 4 ✔

Return true

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

---

4. Better Approach

There is no better approach.

The Brute Force approach itself is optimal because we may need to inspect every element once to verify that the array is sorted.

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

---

5. Optimal Approach

The same single-pass traversal is the optimal solution.

Observation

For a sorted array:

arr[i] >= arr[i - 1]

must hold true for every index from 1 to n-1.

If this condition is violated even once:

arr[i] < arr[i - 1]

the array is not sorted.

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

---

6. Common Mistakes

Mistake 1

Starting iteration from index 0.

Index 0 has no previous element.

Correct:

Start from index 1.

---

Mistake 2

Using the wrong comparison.

Wrong:

if(arr[i] > arr[i - 1])

Correct:

if(arr[i] < arr[i - 1])

---

Mistake 3

Forgetting that duplicates are allowed.

Example:

[1,2,2,3,4]

This array is sorted.

---

Mistake 4

Returning true before checking all elements.

Always complete the traversal before returning true.

---

7. Code

Optimal Approach

public static boolean isSorted(int[] arr) {

```
for(int i = 1; i < arr.length; i++) {

    if(arr[i] < arr[i - 1]) {
        return false;
    }
}

return true;
```

}

---

8. Problem Link

Practice Problem:

https://www.geeksforgeeks.org/check-if-an-array-is-sorted/

---

9. YouTube Link

YouTube Video:

(Paste your YouTube video link here)

