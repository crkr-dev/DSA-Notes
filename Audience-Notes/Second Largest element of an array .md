Second Largest Element in an Array

1. Problem Statement

Given an array of integers, find and return the second largest element present in the array.

If the second largest element does not exist, return -1.

---

2. Problem Explanation

We need to find the element that is smaller than the largest element but greater than all other elements.

Example

Input:

nums = [1,2,4,7,7,5]

Output:

5

Explanation:

Largest Element = 7

Second Largest Element = 5

---

3. Intuition (Brute Force)

Sort the array in ascending order.

The largest element will be at the end.

Traverse backwards and find the first element that is not equal to the largest element.

Example

nums = [1,2,4,7,7,5]

After Sorting:

[1,2,4,5,7,7]

Largest = 7

Traverse from end:

7 = 7 → Skip

7 = 7 → Skip

5 ≠ 7 → Answer

Second Largest = 5

Complexity

Time Complexity : O(n log n)

Space Complexity : O(1)

---

4. Better Approach

Observation:

We do not need to sort the array.

First find the largest element.

Traverse again and find the largest element smaller than the largest.

Complexity

Time Complexity : O(2n)

Space Complexity : O(1)

---

5. Optimal Approach

Pattern:

Array Traversal

Largest and Second Largest Tracking

Observation:

Maintain:

largest

secondLargest

While traversing:

If current element > largest

Update secondLargest = largest

Update largest = current element

---

Else if

current element > secondLargest

and

current element != largest

Update secondLargest

Example

nums = [1,2,4,7,7,5]

Initial:

largest = 1

secondLargest = -1

---

2

largest = 2

secondLargest = 1

---

4

largest = 4

secondLargest = 2

---

7

largest = 7

secondLargest = 4

---

7

No update

---

5

secondLargest = 5

Answer = 5

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

---

6. Common Mistakes

Mistake 1

Not handling duplicate largest elements.

Example:

[7,7,7]

There is no second largest element.

---

Mistake 2

Initializing secondLargest incorrectly.

---

Mistake 3

Updating secondLargest when current element equals largest.

---

Mistake 4

Sorting the array when a single traversal is sufficient.

---

7. Code

Brute Force Approach (Sorting)

```java id="pnhl1d"
public int secondLargest(int[] nums) {

    Arrays.sort(nums);

    int largest = nums[nums.length - 1];

    for(int i = nums.length - 2; i >= 0; i--) {

        if(nums[i] != largest) {
            return nums[i];
        }
    }

    return -1;
}
```

---

Better Approach

```java id="m3v92r"
public int secondLargest(int[] nums) {

    int largest = nums[0];

    for(int num : nums) {

        largest = Math.max(largest, num);
    }

    int secondLargest = -1;

    for(int num : nums) {

        if(num > secondLargest && num != largest) {

            secondLargest = num;
        }
    }

    return secondLargest;
}
```

---

Optimal Approach

```java id="qv7o1f"
public int secondLargest(int[] nums) {

    int largest = nums[0];
    int secondLargest = -1;

    for(int i = 1; i < nums.length; i++) {

        if(nums[i] > largest) {

            secondLargest = largest;
            largest = nums[i];

        } else if(nums[i] > secondLargest &&
                  nums[i] != largest) {

            secondLargest = nums[i];
        }
    }

    return secondLargest;
}
```

---

8. Pattern Recognition

Pattern:

Array Traversal

Largest and Second Largest Tracking

Observation:

Track the two largest elements while traversing.

No sorting required.

Trigger Words:

* Second Largest
* Second Maximum
* Runner Up
* Largest and Second Largest

Think:

Can I maintain both largest and second largest simultaneously?

---

9. Problem Link

Second Largest Element in an Array

https://www.geeksforgeeks.org/problems/second-largest3735/1

---

10. YouTube Link

YouTube Video:

(Paste your YouTube video link here)
