Problem: Right Rotate Array by D Places

Pattern:
Array Manipulation
Reversal Technique

Problem Link:
https://leetcode.com/problems/rotate-array/

Observation:
After rotating right by d places:
- Last d elements move to the front.
- Remaining elements shift right.

Approaches:

1. Brute Force
- Rotate right by one place d times.
- TC: O(n*d)
- SC: O(1)

2. Better
- Store last d elements in temp array.
- Shift remaining elements right.
- Place temp elements at beginning.
- TC: O(n)
- SC: O(d)

3. Optimal (Reversal Algorithm)
- Reverse entire array.
- Reverse first d elements.
- Reverse remaining n-d elements.
- TC: O(n)
- SC: O(1)

Dry Run:

arr = [1,2,3,4,5,6,7]
d = 2

Reverse Entire Array

[7,6,5,4,3,2,1]

Reverse First d Elements

[6,7,5,4,3,2,1]

Reverse Remaining Elements

[6,7,1,2,3,4,5]

Important:
d = d % n

Mistakes I Can Make:
- Forget d = d % n
- Wrong reverse boundaries
- Confuse left and right rotation
- Wrong shifting direction in Better Approach

Pseudo Code (Optimal):

reverse(0,n-1)

reverse(0,d-1)

reverse(d,n-1)

What Should Trigger This Pattern?

Keywords:
- Rotate Array
- Right Rotation
- In-place Rotation
- O(1) Space Rotation

Revision Line:

Right Rotation + O(1) Space = Reverse Whole Array First
