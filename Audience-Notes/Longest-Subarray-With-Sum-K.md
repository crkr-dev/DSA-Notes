Longest Subarray with Sum K

1. Problem Statement

Given an array of positive integers nums and an integer K, find the length of the longest subarray whose sum is equal to K.

---

2. Problem Explanation

We need to find a continuous subarray whose sum equals K.

Among all such subarrays, return the maximum length.

Example

Input:

nums = [1,2,3,1,1,1,1,4,2,3]

K = 3

Output:

3

Explanation:

Subarrays with sum 3:

[1,2] → Length = 2

[3] → Length = 1

[1,1,1] → Length = 3

Maximum Length = 3

---

3. Intuition (Brute Force)

Generate all possible subarrays.

For every subarray:

* Calculate its sum.
* If sum equals K:

  * Calculate its length.
  * Update the maximum length.

Example

nums = [1,2,3]

K = 3

Subarrays:

[1] → 1

[1,2] → 3 ✔

[1,2,3] → 6

[2] → 2

[2,3] → 5

[3] → 3 ✔

Maximum Length = 2

Complexity

Time Complexity : O(n²)

Space Complexity : O(1)

---

4. Better Approach

Observation:

Instead of recalculating the sum every time,

maintain a running sum while expanding the subarray.

For every starting index:

Keep adding elements towards the right.

Whenever sum becomes K:

Update maximum length.

Complexity

Time Complexity : O(n²)

Space Complexity : O(1)

---

5. Optimal Approach

Pattern:

Sliding Window

Two Pointers

Observation:

Since all numbers are positive:

* Expanding the window increases the sum.
* Shrinking the window decreases the sum.

Maintain:

left

right

currentSum

Rules:

If currentSum < K

Expand the window.

---

If currentSum > K

Shrink the window from the left.

---

If currentSum == K

Update maximum length.

Continue exploring.

Example

nums = [1,2,3,1,1]

K = 3

Window:

[1]

Sum = 1

Expand

---

[1,2]

Sum = 3

Length = 2

Answer = 2

---

[1,2,3]

Sum = 6

Shrink

---

[2,3]

Sum = 5

Shrink

---

[3]

Sum = 3

Length = 1

Answer = 2

Final Answer = 2

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

---

6. Common Mistakes

Mistake 1

Applying Sliding Window when negative numbers exist.

Sliding Window works only because all numbers are positive.

---

Mistake 2

Forgetting to shrink when sum becomes greater than K.

---

Mistake 3

Updating answer only once.

Update every time sum equals K.

---

Mistake 4

Using nested loops even after recognizing the Sliding Window pattern.

---

7. Code

Brute Force Approach

```java
public int longestSubarray(int[] nums, int k) {

    int maxLen = 0;

    for(int i = 0; i < nums.length; i++) {

        int sum = 0;

        for(int j = i; j < nums.length; j++) {

            sum += nums[j];

            if(sum == k) {

                maxLen = Math.max(maxLen, j - i + 1);
            }
        }
    }

    return maxLen;
}
```

---

Optimal Approach (Sliding Window)

```java
public int longestSubarray(int[] nums, int k) {

    int left = 0;
    int right = 0;

    long sum = nums[0];

    int maxLen = 0;

    while(right < nums.length) {

        while(left <= right && sum > k) {

            sum -= nums[left];
            left++;
        }

        if(sum == k) {

            maxLen = Math.max(maxLen,
                              right - left + 1);
        }

        right++;

        if(right < nums.length) {

            sum += nums[right];
        }
    }

    return maxLen;
}
```

---

8. Pattern Recognition

Pattern:

Sliding Window

Two Pointers

Observation:

All numbers are positive.

Window sum increases when expanded.

Window sum decreases when shrunk.

Trigger Words:

* Longest Subarray
* Sum Equals K
* Positive Numbers
* Continuous Subarray

Think:

Can Sliding Window work?

Can I maintain a running sum?

Can I expand and shrink the window?

---

9. Problem Link

GeeksforGeeks - Longest Subarray with Sum K

https://www.geeksforgeeks.org/problems/longest-sub-array-with-sum-k0809/1

10. YouTube Link

YouTube Video:

(Paste your YouTube video link here)

