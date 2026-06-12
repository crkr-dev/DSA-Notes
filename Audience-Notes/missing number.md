Missing Number

1. Problem Statement

Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.

---

2. Problem Explanation

The array contains numbers from 0 to n.

Exactly one number is missing.

Our task is to find the missing number.

Example 1

Input:

nums = [3,0,1]

Output:

2

Explanation:

Numbers from 0 to 3 are:

0,1,2,3

Array contains:

0,1,3

Missing number is:

2

---

Example 2

Input:

nums = [0,1]

Output:

2

Explanation:

Numbers from 0 to 2 are:

0,1,2

Missing number is:

2

---

3. Intuition (Brute Force)

Sort the array.

After sorting, every number should be present at its corresponding index.

If nums[i] != i, then i is the missing number.

Example

nums = [3,0,1]

After sorting:

[0,1,3]

Check:

nums[0] = 0 ✔

nums[1] = 1 ✔

nums[2] = 3 ✘

Missing number = 2

Complexity

Time Complexity : O(n log n)

Space Complexity : O(1)

---

4. Better Approach

Using HashSet

Store all elements in a HashSet.

Traverse numbers from 0 to n.

The first number not present in the HashSet is the answer.

Example

nums = [3,0,1]

HashSet:

{0,1,3}

Check:

0 ✔

1 ✔

2 ✘

Missing number = 2

Complexity

Time Complexity : O(n)

Space Complexity : O(n)

---

5. Optimal Approach 1 (Math Formula)

Pattern:

Mathematical Observation

Observation:

Numbers are from 0 to n.

Sum of numbers from 0 to n:

n × (n + 1) / 2

Missing Number:

Expected Sum - Actual Sum

Example

nums = [3,0,1]

n = 3

Expected Sum:

3 × 4 / 2 = 6

Actual Sum:

3 + 0 + 1 = 4

Missing Number:

6 - 4 = 2

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

---

6. Optimal Approach 2 (XOR)

Pattern:

Bit Manipulation

Observation:

a ^ a = 0

a ^ 0 = a

If we XOR all numbers from 0 to n and all array elements, every matching number cancels out.

The remaining value is the missing number.

Example

nums = [3,0,1]

(0 ^ 1 ^ 2 ^ 3) ^ (3 ^ 0 ^ 1)

All matching numbers cancel.

Remaining:

2

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

---

7. Optimal Approach 3 (Cyclic Sort)

Pattern:

Cyclic Sort

Observation:

Each number belongs to its own index.

0 -> index 0

1 -> index 1

2 -> index 2

3 -> index 3

Place every number at its correct position.

After placement:

If nums[i] != i

Then i is the missing number.

Example

nums = [3,0,1]

After cyclic sort:

[0,1,3]

Check:

nums[0] = 0 ✔

nums[1] = 1 ✔

nums[2] = 3 ✘

Missing number = 2

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

---

8. Common Mistakes

Mistake 1

Forgetting that the range is [0, n].

The missing number can be n itself.

Example:

nums = [0,1]

Answer = 2

---

Mistake 2

Using integer types incorrectly while calculating the formula.

For larger values, use long if required.

---

Mistake 3

Incorrect swapping logic in Cyclic Sort.

Always verify the target index before swapping.

---

Mistake 4

Forgetting to XOR with all numbers from 0 to n.

---

9. Code

Brute Force Approach (Sorting)

```java
public int missingNumber(int[] nums) {

    Arrays.sort(nums);

    for(int i = 0; i < nums.length; i++) {

        if(nums[i] != i) {
            return i;
        }
    }

    return nums.length;
}
```

---

Better Approach (HashSet)

```java
public int missingNumber(int[] nums) {

    HashSet<Integer> set = new HashSet<>();

    for(int num : nums) {
        set.add(num);
    }

    for(int i = 0; i <= nums.length; i++) {

        if(!set.contains(i)) {
            return i;
        }
    }

    return -1;
}
```

---

Optimal Approach 1 (Math Formula)

```java
public int missingNumber(int[] nums) {

    int n = nums.length;

    int expected = n * (n + 1) / 2;

    int actual = 0;

    for(int num : nums) {
        actual += num;
    }

    return expected - actual;
}
```

---

Optimal Approach 2 (XOR)

```java
public int missingNumber(int[] nums) {

    int xor = nums.length;

    for(int i = 0; i < nums.length; i++) {

        xor ^= i;
        xor ^= nums[i];
    }

    return xor;
}
```

---

10. Pattern Recognition

Pattern 1:

Mathematical Formula

Trigger Words:

* Missing Number
* Range [0,n]
* One Missing Element

---

Pattern 2:

Bit Manipulation (XOR)

Trigger Words:

* Missing Number
* O(1) Space
* No Extra Data Structure

---

Pattern 3:

Cyclic Sort

Trigger Words:

* Numbers belong to indices
* Missing Number
* Range Based Numbers

---

11. Problem Link

LeetCode 268 - Missing Number

https://leetcode.com/problems/missing-number/

---

12. YouTube Link

YouTube Video:

(Paste your YouTube video link here)
