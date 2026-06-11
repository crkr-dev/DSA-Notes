
Problem: Check if Array is Sorted

Pattern:
Array Traversal

Problem Link:
https://www.geeksforgeeks.org/check-if-an-array-is-sorted/

Observation:
For a sorted array, every element should be greater than or equal to its previous element.

Condition:

arr[i] >= arr[i - 1]

If any element violates this condition, the array is not sorted.

Approaches:

1. Single Pass Traversal (Optimal)

* Start from index 1.
* Compare current element with previous element.
* If current element is smaller than previous element, return false.
* If traversal completes, return true.

TC: O(n)

SC: O(1)

Dry Run:

arr = [1,2,3,4,5]

2 >= 1 ✔

3 >= 2 ✔

4 >= 3 ✔

5 >= 4 ✔

Return true

---

arr = [1,3,2,4,5]

3 >= 1 ✔

2 >= 3 ✘

Return false

Important:

Sorted Array Condition:

arr[i] >= arr[i - 1]

Duplicates are allowed.

Example:

[1,2,2,3,4]

is sorted.

Mistakes I Can Make:

* Starting iteration from index 0.
* Using wrong comparison operator.
* Forgetting duplicates are allowed.
* Writing arr[i] > arr[i - 1] instead of checking for violation.
* Returning true before completing traversal.

Pseudo Code:

for(i = 1 to n-1)

```
if(arr[i] < arr[i-1])

    return false
```

return true

What Should Trigger This Pattern?

Keywords:

* Check
* Verify
* Validate
* Determine
* Is Sorted
* Ascending Order

Revision Line:

Whenever the question asks whether an array is sorted, compare every element with its previous element and look for the first violation.
