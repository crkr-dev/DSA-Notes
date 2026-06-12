Problem: Missing Number

Pattern:
Math Formula
Cyclic Sort
Bit Manipulation (XOR)

Problem Link:
https://leetcode.com/problems/missing-number/

Observation:

Array contains n distinct numbers from the range [0, n].

Exactly one number is missing.

Approaches:

1. Sorting

* Sort the array.
* Traverse from index 0.
* If nums[i] != i, then i is the missing number.
* If all positions are correct, answer is n.

TC: O(n log n)

SC: O(1) or O(log n) depending on sorting algorithm.

---

2. HashSet

* Store all elements in a HashSet.
* Check numbers from 0 to n.
* First missing number is the answer.

TC: O(n)

SC: O(n)

---

3. Math Formula

Expected Sum:

n * (n + 1) / 2

Actual Sum:

Sum of all elements in array.

Missing Number:

Expected Sum - Actual Sum

TC: O(n)

SC: O(1)

---

4. XOR

Observation:

a ^ a = 0

a ^ 0 = a

XOR all numbers from 0 to n.

XOR all array elements.

Remaining value is the missing number.

TC: O(n)

SC: O(1)

---

5. Cyclic Sort

Observation:

Every number belongs to its own index.

0 -> index 0

1 -> index 1

2 -> index 2

...

Place every element at its correct position.

After placement:

If nums[i] != i

Then i is the missing number.

If all positions are correct:

Answer = n

TC: O(n)

SC: O(1)

Dry Run:

nums = [3,0,1]

Expected numbers:

0,1,2,3

Expected Sum:

3 * 4 / 2 = 6

Actual Sum:

3 + 0 + 1 = 4

Missing:

6 - 4 = 2

Answer = 2

Important:

Formula:

n * (n + 1) / 2

XOR Properties:

a ^ a = 0

a ^ 0 = a

Mistakes I Can Make:

* Forgetting range is [0, n].
* Returning wrong value when answer is n.
* Integer overflow in formula for large values.
* Incorrect cyclic sort swapping conditions.
* Forgetting XOR with n.

Pseudo Code (Formula):

expected = n * (n + 1) / 2

actual = sum(nums)

return expected - actual

What Should Trigger This Pattern?

Pattern 1:
Math Formula

Trigger Words:

* Missing Number
* Range [0,n]
* One Missing Element

---

Pattern 2:
Cyclic Sort

Trigger Words:

* Numbers belong to indices
* Range Based Numbers
* Missing Number

---

Pattern 3:
XOR

Trigger Words:

* Missing Number
* O(1) Space
* No Extra Data Structure

Revision Line:

Range [0,n] + One Missing Number = Think Formula, XOR, or Cyclic Sort.
