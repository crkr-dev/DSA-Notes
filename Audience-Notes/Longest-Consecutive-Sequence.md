Longest Consecutive Sequence

1. Problem Statement

Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in O(n) time.

---

2. Problem Explanation

We need to find the longest sequence of consecutive numbers present in the array.

The numbers do not need to be adjacent in the array.

They only need to be consecutive in value.

Example

Input:

nums = [100,4,200,1,3,2]

Output:

4

Explanation:

The consecutive sequence is:

1,2,3,4

Length = 4

---

3. Intuition (Brute Force)

For every element:

Check whether the next consecutive number exists.

Continue checking until the sequence breaks.

Keep track of the maximum sequence length.

Example

nums = [100,4,200,1,3,2]

Start from 1:

1 → 2 → 3 → 4

Length = 4

Start from 100:

Length = 1

Start from 200:

Length = 1

Maximum Length = 4

Complexity

Time Complexity : O(n²)

Space Complexity : O(1)

---

4. Better Approach

Pattern:

Sorting

Observation:

If we sort the array:

nums = [1,2,3,4,100,200]

Now consecutive numbers become adjacent.

Traverse the sorted array:

* If current = previous + 1
  increase count.
* Otherwise start a new sequence.

Keep track of the maximum length.

Complexity

Time Complexity : O(n log n)

Space Complexity : O(1)

---

5. Optimal Approach

Pattern:

HashSet

Sequence Start Detection

Observation:

Store all numbers in a HashSet.

For every number:

Check whether:

num - 1

exists in the set.

If it exists:

This is not the start of a sequence.

Skip it.

---

If num - 1 does not exist:

This is the start of a sequence.

Start expanding:

num

num + 1

num + 2

...

until the sequence breaks.

Example

nums = [100,4,200,1,3,2]

HashSet:

{100,4,200,1,3,2}

---

Number = 1

0 not present

Start sequence:

1 → 2 → 3 → 4

Length = 4

---

Number = 2

1 present

Not a starting point

Skip

---

Number = 3

2 present

Skip

---

Number = 4

3 present

Skip

Answer = 4

Complexity

Time Complexity : O(n)

Space Complexity : O(n)

---

6. Common Mistakes

Mistake 1

Starting a sequence from every element.

This causes unnecessary work.

---

Mistake 2

Forgetting to check:

num - 1

before starting a sequence.

---

Mistake 3

Not handling duplicates properly.

HashSet automatically removes duplicates.

---

Mistake 4

Using sorting when the question specifically asks for O(n).

---

7. Code

Brute Force Approach

```java id="0z6dci"
public int longestConsecutive(int[] nums) {

    int longest = 0;

    for(int num : nums) {

        int current = num;
        int count = 1;

        while(contains(nums, current + 1)) {

            current++;
            count++;
        }

        longest = Math.max(longest, count);
    }

    return longest;
}

private boolean contains(int[] nums, int target) {

    for(int num : nums) {

        if(num == target) {
            return true;
        }
    }

    return false;
}
```

---

Better Approach (Sorting)

```java id="b8nt8n"
public int longestConsecutive(int[] nums) {

    if(nums.length == 0) {
        return 0;
    }

    Arrays.sort(nums);

    int longest = 1;
    int currentCount = 1;

    for(int i = 1; i < nums.length; i++) {

        if(nums[i] == nums[i - 1]) {
            continue;
        }

        if(nums[i] == nums[i - 1] + 1) {

            currentCount++;

        } else {

            longest = Math.max(longest, currentCount);
            currentCount = 1;
        }
    }

    return Math.max(longest, currentCount);
}
```

---

Optimal Approach (HashSet)

```java id="w4jz7u"
public int longestConsecutive(int[] nums) {

    HashSet<Integer> set = new HashSet<>();

    for(int num : nums) {
        set.add(num);
    }

    int longest = 0;

    for(int num : set) {

        if(!set.contains(num - 1)) {

            int currentNum = num;
            int count = 1;

            while(set.contains(currentNum + 1)) {

                currentNum++;
                count++;
            }

            longest = Math.max(longest, count);
        }
    }

    return longest;
}
```

---

8. Pattern Recognition

Pattern:

HashSet

Sequence Start Detection

Observation:

A sequence should only be started from its smallest element.

If:

num - 1

exists,

then the sequence already started earlier.

Trigger Words:

* Longest Consecutive
* Consecutive Sequence
* Unsorted Array
* O(n) Requirement

Think:

Can I use a HashSet?

Can I identify only the starting points?

Can I expand the sequence from there?

---

9. Problem Link

LeetCode 128 - Longest Consecutive Sequence

https://leetcode.com/problems/longest-consecutive-sequence/

---

10. YouTube Link

YouTube Video:

(Paste your YouTube video link here)
