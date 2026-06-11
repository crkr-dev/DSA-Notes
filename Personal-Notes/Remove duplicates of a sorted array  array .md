Problem: Remove Duplicates from Sorted Array

Pattern:
Two Pointers
In-place Array Modification

Problem Link:
https://leetcode.com/problems/remove-duplicates-from-sorted-array/

Observation:
The array is already sorted.

Therefore, duplicate elements will always be adjacent.

We only need to keep track of the last unique element and place the next unique element after it.

Approaches:

1. Using HashSet / ArrayList

* Store unique elements.
* Copy them back to the original array.
* Return the count.

TC: O(n)

SC: O(n)

---

2. Using Extra Array + Two Pointers

* Traverse the array.
* Store unique elements in another array.
* Return count of unique elements.

TC: O(n)

SC: O(n)

---

3. Optimal Approach (In-place Two Pointers)

* One pointer tracks the position of the last unique element.
* Another pointer traverses the array.
* Whenever a new unique element is found:

  * Move unique pointer.
  * Place current element at unique pointer position.

TC: O(n)

SC: O(1)

Dry Run:

nums = [1,1,2,2,3]

i = 0

j = 1

1 == 1

Duplicate

Ignore

---

j = 2

2 != 1

i++

nums[i] = nums[j]

Array:

[1,2,2,2,3]

---

j = 3

2 == 2

Duplicate

Ignore

---

j = 4

3 != 2

i++

nums[i] = nums[j]

Array:

[1,2,3,2,3]

Unique Elements:

[1,2,3]

Return:

i + 1 = 3

Important:

* Array is sorted.
* Duplicates are adjacent.
* Only first k elements matter.
* Elements after k can be anything.

Mistakes I Can Make:

* Forgetting array is sorted.
* Returning i instead of i + 1.
* Comparing with previous index instead of last unique index.
* Moving unique pointer for duplicates.
* Using extra space when in-place solution is required.

Pseudo Code:

i = 0

for(j = 1 to n-1)

```
if(nums[j] != nums[i])

    i++

    nums[i] = nums[j]
```

return i + 1

What Should Trigger This Pattern?

Keywords:

* Sorted Array
* Remove Duplicates
* Unique Elements
* In-place
* O(1) Space

Revision Line:

Sorted Array + Remove Duplicates + In-place = Two Pointers
