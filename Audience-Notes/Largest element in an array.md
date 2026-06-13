Largest Element in an Array

1. Problem Statement

Given an array of integers, find and return the largest element present in the array.

---

2. Problem Explanation

We need to find the maximum value present in the array.

Example

Input:

nums = [2,5,1,3,0]

Output:

5

Explanation:

Among all elements, 5 is the largest.

---

3. Intuition (Brute Force)

Sort the array in ascending order.

The last element of the sorted array will be the largest element.

Example

nums = [2,5,1,3,0]

After Sorting:

[0,1,2,3,5]

Largest Element = 5

Complexity

Time Complexity : O(n log n)

Space Complexity : O(1)

---

4. Better Approach

Observation:

We do not need to sort the entire array.

We only need the maximum element.

Traverse the array and keep track of the largest element found so far.

---

5. Optimal Approach

Pattern:

Array Traversal

Maximum So Far

Observation:

Assume the first element is the largest.

Traverse the remaining array.

Whenever a larger element is found:

Update the largest element.

Example

nums = [2,5,1,3,0]

Initial:

largest = 2

---

5 > 2

largest = 5

---

1 < 5

No update

---

3 < 5

No update

---

0 < 5

No update

Answer = 5

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

---

6. Common Mistakes

Mistake 1

Initializing largest with 0.

This fails for arrays containing negative numbers.

---

Mistake 2

Sorting the array when only the maximum element is required.

---

Mistake 3

Forgetting to compare every element.

---

7. Code

Brute Force Approach (Sorting)

```java
public int largestElement(int[] nums) {

    Arrays.sort(nums);

    return nums[nums.length - 1];
}
```

---

Optimal Approach

```java
public int largestElement(int[] nums) {

    int largest = nums[0];

    for(int i = 1; i < nums.length; i++) {

        if(nums[i] > largest) {

            largest = nums[i];
        }
    }

    return largest;
}
```

---

8. Pattern Recognition

Pattern:

Array Traversal

Maximum So Far

Observation:

We only need the largest value.

Maintain the maximum seen so far while traversing.

Trigger Words:

* Largest Element
* Maximum Element
* Highest Value
* Maximum Number

Think:

Can I keep track of the maximum while traversing?

---

9. Problem Link

Largest Element in an Array

https://www.geeksforgeeks.org/problems/largest-element-in-array4009/1

---

10. YouTube Link

YouTube Video:

(Paste your YouTube video link here)
