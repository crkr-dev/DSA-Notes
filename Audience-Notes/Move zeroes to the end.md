Move Zeroes to the End

1. Problem Statement

Given an integer array nums, move all 0's to the end of the array while maintaining the relative order of the non-zero elements.

You must do this in-place without making a copy of the array.

---

2. Problem Explanation

We need to move all zeroes to the end.

The order of non-zero elements should remain unchanged.

Example

Input:

nums = [0,1,0,3,12]

Output:

[1,3,12,0,0]

Explanation:

Non-zero elements:

1,3,12

Maintain their order and place all zeroes at the end.

---

3. Intuition (Brute Force)

Create a temporary array.

First store all non-zero elements.

Then fill the remaining positions with zeroes.

Example

nums = [0,1,0,3,12]

Step 1:

Store non-zero elements:

[1,3,12]

Step 2:

Fill remaining positions with zeroes.

Result:

[1,3,12,0,0]

Complexity

Time Complexity : O(n)

Space Complexity : O(n)

---

4. Better Approach

Observation:

We only need to know where the next non-zero element should be placed.

Maintain an index pointing to the next position for a non-zero element.

Traverse the array:

Whenever a non-zero element is found,

place it at the correct position.

Fill the remaining positions with zeroes.

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

---

5. Optimal Approach

Pattern:

Two Pointers

In-Place Swapping

Observation:

Find the first zero.

After that:

Whenever a non-zero element is found,

swap it with the zero position.

Move both pointers accordingly.

Example

nums = [1,0,2,3,0,4,0,1]

---

First zero at index 1

j = 1

i = 2

---

nums[2] = 2

Swap

[1,2,0,3,0,4,0,1]

j = 2

---

nums[3] = 3

Swap

[1,2,3,0,0,4,0,1]

j = 3

---

nums[5] = 4

Swap

[1,2,3,4,0,0,0,1]

j = 4

---

nums[7] = 1

Swap

[1,2,3,4,1,0,0,0]

Answer:

[1,2,3,4,1,0,0,0]

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

---

6. Common Mistakes

Mistake 1

Not preserving the order of non-zero elements.

---

Mistake 2

Using sorting.

Sorting changes the order of elements.

---

Mistake 3

Using extra space when the problem asks for in-place modification.

---

Mistake 4

Swapping every element unnecessarily.

Only swap when a non-zero element is found after a zero.

---

7. Code

Brute Force Approach

```java
public void moveZeroes(int[] nums) {

    int[] temp = new int[nums.length];

    int index = 0;

    for(int num : nums) {

        if(num != 0) {

            temp[index++] = num;
        }
    }

    while(index < nums.length) {

        temp[index++] = 0;
    }

    for(int i = 0; i < nums.length; i++) {

        nums[i] = temp[i];
    }
}
```

---

Optimal Approach (Two Pointers)

```java
public void moveZeroes(int[] nums) {

    int j = -1;

    for(int i = 0; i < nums.length; i++) {

        if(nums[i] == 0) {

            j = i;
            break;
        }
    }

    if(j == -1) {
        return;
    }

    for(int i = j + 1; i < nums.length; i++) {

        if(nums[i] != 0) {

            int temp = nums[i];
            nums[i] = nums[j];
            nums[j] = temp;

            j++;
        }
    }
}
```

---

8. Pattern Recognition

Pattern:

Two Pointers

In-Place Swapping

Observation:

Find the position where the next non-zero element should go.

Swap non-zero elements forward.

Trigger Words:

* Move Zeroes
* Shift Elements
* Maintain Order
* In Place
* Rearrange Array

Think:

Can I use two pointers?

Can I move elements without using extra space?

---

9. Problem Link

LeetCode 283 - Move Zeroes

https://leetcode.com/problems/move-zeroes/

---

10. YouTube Link

YouTube Video:

(Paste your YouTube video link here)
