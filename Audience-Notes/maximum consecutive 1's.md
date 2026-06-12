Maximum Consecutive Ones

1. Problem Statement

Given a binary array nums, return the maximum number of consecutive 1's in the array.

---

2. Problem Explanation

We need to find the longest continuous sequence of 1's present in the array.

Example

Input:

nums = [1,1,0,1,1,1]

Output:

3

Explanation:

Consecutive sequences of 1's are:

[1,1] → Length = 2

[1,1,1] → Length = 3

Maximum Consecutive Ones = 3

---

3. Intuition (Brute Force)

Generate all possible subarrays.

For each subarray:

* Check whether every element is 1.
* If yes, calculate its length.
* Update the maximum length.

Example

nums = [1,1,0,1]

Subarrays:

[1]

[1,1]

[1,1,0]

[1]

[1,0]

[0]

[0,1]

[1]

Among valid subarrays containing only 1's:

[1]

[1,1]

[1]

Maximum Length = 2

Complexity

Time Complexity : O(n²) to O(n³)

Space Complexity : O(1)

---

4. Better Approach

Observation:

We do not need to generate all subarrays.

We only care about the current streak of consecutive 1's.

Maintain:

currentCount

Whenever we see a 1:

currentCount++

Whenever we see a 0:

currentCount = 0

Update maximum count during traversal.

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

---

5. Optimal Approach

Pattern:

Array Traversal

Running Count

Longest Streak

Observation:

A 0 breaks the sequence of consecutive 1's.

Therefore:

* Count consecutive 1's.
* Reset count whenever a 0 is found.
* Maintain the maximum streak seen so far.

Example

nums = [1,1,0,1,1,1]

Step 1

1

currentCount = 1

maxCount = 1

---

Step 2

1

currentCount = 2

maxCount = 2

---

Step 3

0

currentCount = 0

---

Step 4

1

currentCount = 1

maxCount = 2

---

Step 5

1

currentCount = 2

maxCount = 2

---

Step 6

1

currentCount = 3

maxCount = 3

Answer = 3

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

---

6. Common Mistakes

Mistake 1

Forgetting to reset count when encountering 0.

Wrong:

Continue counting after 0.

Correct:

currentCount = 0

---

Mistake 2

Updating maxCount only at the end.

Update maxCount during every iteration.

---

Mistake 3

Trying to generate all subarrays.

Only the current streak matters.

---

Mistake 4

Using extra arrays or extra data structures.

Not required.

---

7. Code

Brute Force Approach

```java
public int findMaxConsecutiveOnes(int[] nums) {

    int maxLen = 0;

    for(int i = 0; i < nums.length; i++) {

        for(int j = i; j < nums.length; j++) {

            boolean valid = true;

            for(int k = i; k <= j; k++) {

                if(nums[k] == 0) {
                    valid = false;
                    break;
                }
            }

            if(valid) {
                maxLen = Math.max(maxLen, j - i + 1);
            }
        }
    }

    return maxLen;
}
```

---

Optimal Approach

```java
public int findMaxConsecutiveOnes(int[] nums) {

    int currentCount = 0;
    int maxCount = 0;

    for(int num : nums) {

        if(num == 1) {

            currentCount++;

            maxCount = Math.max(maxCount, currentCount);

        } else {

            currentCount = 0;
        }
    }

    return maxCount;
}
```

---

8. Pattern Recognition

Pattern:

Array Traversal

Running Count

Longest Streak

Observation:

A zero breaks the sequence.

A one extends the sequence.

Trigger Words:

* Consecutive
* Continuous
* Longest Consecutive
* Maximum Consecutive
* Longest Streak

Think:

Maintain Current Count

Reset on Break

Track Maximum

---

9. Problem Link

LeetCode 485 - Maximum Consecutive Ones

https://leetcode.com/problems/max-consecutive-ones/

---

10. YouTube Link

YouTube Video:

(Paste your YouTube video link here)
