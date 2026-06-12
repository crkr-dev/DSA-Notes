Two Sum

1. Problem Statement

Given an array of integers nums and an integer target, return the indices of the two numbers such that they add up to the target.

You may assume that each input has exactly one solution, and you may not use the same element twice.

Return the answer in any order.

---

2. Problem Explanation

We need to find two numbers whose sum equals the target.

Instead of returning the numbers, we must return their indices.

Example

Input:

nums = [2,7,11,15]

target = 9

Output:

[0,1]

Explanation:

nums[0] + nums[1]

2 + 7 = 9

Therefore return:

[0,1]

---

3. Intuition (Brute Force)

Generate all possible pairs.

For every pair:

Check whether:

nums[i] + nums[j] == target

If yes:

Return the indices.

Example

nums = [2,7,11,15]

Check:

2 + 7 = 9 ✔

Answer:

[0,1]

Complexity

Time Complexity : O(n²)

Space Complexity : O(1)

---

4. Better Approach

Observation:

For every element x,

we need:

target - x

Instead of searching the entire array again, we can store previously seen elements in a HashMap.

HashMap stores:

Value → Index

While traversing:

Check whether the required complement already exists.

If yes:

Answer found.

Complexity

Time Complexity : O(n)

Space Complexity : O(n)

---

5. Optimal Approach

Pattern:

HashMap

Complement Lookup

Observation:

For every number:

current = nums[i]

Required number:

target - current

If the required number is already present in the HashMap,

we have found the pair.

Example

nums = [2,7,11,15]

target = 9

---

i = 0

current = 2

Required = 7

Not present

Store:

2 → 0

---

i = 1

current = 7

Required = 2

Present in HashMap

Answer:

[0,1]

Complexity

Time Complexity : O(n)

Space Complexity : O(n)

---

6. Common Mistakes

Mistake 1

Using the same element twice.

Wrong:

Using the current element as both numbers.

---

Mistake 2

Adding current element to HashMap before checking complement.

Always check first.

Then insert.

---

Mistake 3

Returning values instead of indices.

Question asks for indices.

---

Mistake 4

Using nested loops even after recognizing the complement pattern.

HashMap gives O(1) lookup.

---

7. Code

Brute Force Approach

```java
public int[] twoSum(int[] nums, int target) {

    for(int i = 0; i < nums.length; i++) {

        for(int j = i + 1; j < nums.length; j++) {

            if(nums[i] + nums[j] == target) {

                return new int[]{i, j};
            }
        }
    }

    return new int[]{};
}
```

---

Optimal Approach (HashMap)

```java
public int[] twoSum(int[] nums, int target) {

    HashMap<Integer, Integer> map = new HashMap<>();

    for(int i = 0; i < nums.length; i++) {

        int complement = target - nums[i];

        if(map.containsKey(complement)) {

            return new int[]{map.get(complement), i};
        }

        map.put(nums[i], i);
    }

    return new int[]{};
}
```

---

8. Pattern Recognition

Pattern:

HashMap

Complement Lookup

Observation:

For every number x,

we need:

target - x

Instead of searching again,

store previously seen elements.

Trigger Words:

* Two Sum
* Pair Sum
* Target Sum
* Find Pair
* Return Indices
* Pair Equals Target

Think:

Can I store previous elements?

Can I find the complement quickly?

HashMap?

---

9. Problem Link

LeetCode 1 - Two Sum

https://leetcode.com/problems/two-sum/

---

10. YouTube Link

YouTube Video:

(Paste your YouTube video link here)
