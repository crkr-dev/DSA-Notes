Problem: Left Rotate Array by D Places

Pattern:
Array Manipulation
Reversal Technique

Problem Link:
https://leetcode.com/problems/rotate-array/

Observation:
After rotating left by d places:
- First d elements move to the end.
- Remaining elements shift left.

Approaches:

1. Brute Force
- Rotate left by one place d times.
- TC: O(n*d)
- SC: O(1)

2. Better
- Store first d elements in temp array.
- Shift remaining elements left.
- Copy temp elements at the end.
- TC: O(n)
- SC: O(d)

3. Optimal (Reversal Algorithm)
- Reverse first d elements.
- Reverse remaining n-d elements.
- Reverse entire array.
- TC: O(n)
- SC: O(1)

Dry Run:

arr = [1,2,3,4,5,6,7]
d = 2

Reverse(0,1)
[2,1,3,4,5,6,7]

Reverse(2,6)
[2,1,7,6,5,4,3]

Reverse(0,6)
[3,4,5,6,7,1,2]

Important:
d = d % n

Mistakes I Can Make:
- Forget d = d % n
- Wrong reverse boundaries
- Confuse left rotation with right rotation
- Incorrect shifting indices in Better Approach

Pseudo Code (Optimal):

reverse(0,d-1)

reverse(d,n-1)

reverse(0,n-1)

What Should Trigger This Pattern?

Keywords:
- Rotate Array
- Left Rotate
- Right Rotate
- In-place Rotation
- O(1) Space Rotation

Revision Line:

Array Rotation + O(1) Space = Think Reversal Algorithm
