Remove Duplicates from Sorted Array

1. Problem Statement

Given a sorted array nums, remove the duplicates in-place such that each unique element appears only once.

Return the number of unique elements.

The relative order of the elements should be maintained.

The first k elements of the array should contain the unique elements, where k is the number of unique elements.

---

2. Problem Explanation

Since the array is already sorted, duplicate elements will always appear next to each other.

Our goal is to keep only one occurrence of each element and place all unique elements at the beginning of the array.

Example 1

Input:

nums = [1,1,2]

Output:

2

Modified Array:

[1,2,_]

Explanation:

Only 1 and 2 are unique.

Therefore, the answer is 2.

---

Example 2

Input:

nums = [0,0,1,1,1,2,2,3,3,4]

Output:

5

Modified Array:

[0,1,2,3,4,*,*,*,*,_]

Explanation:

Unique elements are:

0, 1, 2, 3, 4

Therefore, answer = 5.

---

3. Intuition (Brute Force)

One simple approach is to store all unique elements in a HashSet or ArrayList.

After collecting unique elements:

1. Copy them back to the original array.
2. Return the count of unique elements.

This works but uses extra space.

Complexity

Time Complexity : O(n)

Space Complexity : O(n)

---

4. Better Approach

Use another array to store unique elements.

Traverse the array:

* If the current element is different from the previous element, store it.
* At the end, copy all unique elements back if needed.

This reduces complexity but still uses extra space.

Complexity

Time Complexity : O(n)

Space Complexity : O(n)

---

5. Optimal Approach

Pattern:

Two Pointers

Observation:

Since the array is sorted, duplicates are adjacent.

We can use:

* One pointer to track the last unique element.
* One pointer to traverse the array.

Whenever we find a new unique element:

* Move the unique pointer.
* Place the new unique element at that position.

Example

nums = [1,1,2,2,3]

Initial:

i = 0

j = 1

---

j = 1

nums[j] == nums[i]

Duplicate

Ignore

---

j = 2

nums[j] != nums[i]

Move unique pointer

i++

nums[i] = nums[j]

Array becomes:

[1,2,2,2,3]

---

j = 3

Duplicate

Ignore

---

j = 4

New unique element found

i++

nums[i] = nums[j]

Array becomes:

[1,2,3,2,3]

Unique elements:

[1,2,3]

Return:

i + 1 = 3

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

---

6. Common Mistakes

Mistake 1

Not using the fact that the array is sorted.

Because the array is sorted, duplicates are adjacent.

---

Mistake 2

Returning i instead of i + 1.

i represents the index of the last unique element.

Number of unique elements = i + 1

---

Mistake 3

Moving the unique pointer for duplicates.

Only move the unique pointer when a new unique element is found.

---

Mistake 4

Comparing with the previous index instead of the last unique element.

Always compare with the element at the unique pointer.

---

Mistake 5

Using extra space when the problem specifically asks for an in-place solution.

---

7. Code

Brute Force Approach (Using HashSet)

```java
public int removeDuplicates(int[] nums) {

    HashSet<Integer> set = new HashSet<>();

    for(int num : nums) {
        set.add(num);
    }

    int index = 0;

    for(int num : set) {
        nums[index++] = num;
    }

    return set.size();
}
```

---

Better Approach (Using Extra Array)

```java
public int removeDuplicates(int[] nums) {

    int n = nums.length;

    int[] temp = new int[n];

    int k = 0;

    temp[k++] = nums[0];

    for(int i = 1; i < n; i++) {

        if(nums[i] != nums[i - 1]) {
            temp[k++] = nums[i];
        }
    }

    for(int i = 0; i < k; i++) {
        nums[i] = temp[i];
    }

    return k;
}
```

---

Optimal Approach (Two Pointers)

```java
public int removeDuplicates(int[] nums) {

    int i = 0;

    for(int j = 1; j < nums.length; j++) {

        if(nums[j] != nums[i]) {

            i++;

            nums[i] = nums[j];
        }
    }

    return i + 1;
}
```

---

8. Pattern Recognition

Pattern:

Two Pointers

Observation:

Sorted array means duplicates are adjacent.

Trigger Words:

* Sorted Array
* Remove Duplicates
* Unique Elements
* In-place
* O(1) Space

Whenever you see:

"Sorted Array + Remove Duplicates + In-place"

Think:

Two Pointers

---

9. Problem Link

LeetCode 26 - Remove Duplicates from Sorted Array

https://leetcode.com/problems/remove-duplicates-from-sorted-array/

---

10. YouTube Link

YouTube Video:

(Paste your YouTube video link here)
