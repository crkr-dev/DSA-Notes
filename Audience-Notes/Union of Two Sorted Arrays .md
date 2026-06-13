Union of Two Sorted Arrays

1. Problem Statement

Given two sorted arrays, find the Union of the arrays.

The Union of two arrays is a collection of all distinct elements present in either of the arrays.

Return the union in sorted order.

---

2. Problem Explanation

We need to combine elements from both arrays.

Duplicate elements should appear only once.

Since the arrays are already sorted, we can use this property to solve the problem efficiently.

Example

Input:

arr1 = [1,2,3,4,5]

arr2 = [1,2,3,6,7]

Output:

[1,2,3,4,5,6,7]

Explanation:

Combine both arrays and keep only unique elements.

---

3. Intuition (Brute Force)

Use a Set.

Insert all elements from the first array.

Insert all elements from the second array.

Since Set stores only unique values, duplicates are automatically removed.

Convert the Set into a list and return it.

Example

arr1 = [1,2,3]

arr2 = [2,3,4]

Set:

{1,2,3,4}

Answer:

[1,2,3,4]

Complexity

Time Complexity : O((n + m) log(n + m))

Space Complexity : O(n + m)

---

4. Better Approach

Observation:

Both arrays are already sorted.

Use two pointers.

Compare elements from both arrays.

Add the smaller element to the answer if it is not already present.

Move the corresponding pointer.

Complexity

Time Complexity : O(n + m)

Space Complexity : O(n + m)

---

5. Optimal Approach

Pattern:

Two Pointers

Merge Process

Observation:

Since arrays are sorted:

* Smaller element should be processed first.
* Avoid duplicates while adding to the answer.

Maintain:

i = 0

j = 0

Example

arr1 = [1,2,3,4]

arr2 = [2,3,5]

---

1 < 2

Add 1

i++

---

2 == 2

Add 2 once

i++

j++

---

3 == 3

Add 3 once

i++

j++

---

4 < 5

Add 4

i++

---

Array 1 finished

Add remaining elements from Array 2

Add 5

Answer:

[1,2,3,4,5]

Complexity

Time Complexity : O(n + m)

Space Complexity : O(n + m)

---

6. Common Mistakes

Mistake 1

Adding duplicate elements to the answer.

Always check the last inserted element.

---

Mistake 2

Forgetting to process remaining elements after one array finishes.

---

Mistake 3

Using nested loops.

Sorted arrays allow a two-pointer solution.

---

Mistake 4

Not handling equal elements correctly.

When elements are equal:

Add only once.

Move both pointers.

---

7. Code

Brute Force Approach (Set)

```java id="0zj9ke"
public List<Integer> findUnion(int[] arr1, int[] arr2) {

    Set<Integer> set = new TreeSet<>();

    for(int num : arr1) {
        set.add(num);
    }

    for(int num : arr2) {
        set.add(num);
    }

    return new ArrayList<>(set);
}
```

---

Optimal Approach (Two Pointers)

```java id="zrk1ua"
public List<Integer> findUnion(int[] arr1, int[] arr2) {

    int i = 0;
    int j = 0;

    List<Integer> union = new ArrayList<>();

    while(i < arr1.length && j < arr2.length) {

        if(arr1[i] <= arr2[j]) {

            if(union.size() == 0 ||
               union.get(union.size() - 1) != arr1[i]) {

                union.add(arr1[i]);
            }

            i++;

        } else {

            if(union.size() == 0 ||
               union.get(union.size() - 1) != arr2[j]) {

                union.add(arr2[j]);
            }

            j++;
        }
    }

    while(i < arr1.length) {

        if(union.get(union.size() - 1) != arr1[i]) {

            union.add(arr1[i]);
        }

        i++;
    }

    while(j < arr2.length) {

        if(union.get(union.size() - 1) != arr2[j]) {

            union.add(arr2[j]);
        }

        j++;
    }

    return union;
}
```

---

8. Pattern Recognition

Pattern:

Two Pointers

Merge Process

Observation:

Both arrays are sorted.

We can process them together in a single traversal.

Trigger Words:

* Union
* Sorted Arrays
* Merge
* Distinct Elements
* Two Arrays

Think:

Can I traverse both arrays simultaneously?

Can I use two pointers?

Can I avoid duplicates while merging?

---

9. Problem Link

GeeksforGeeks - Union of Two Sorted Arrays

https://www.geeksforgeeks.org/problems/union-of-two-sorted-arrays3538/1

---

10. YouTube Link

YouTube Video:

(Paste your YouTube video link here)
