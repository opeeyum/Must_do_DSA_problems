# Must do Array Question.
### 1. Two Sum
 > Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
 > 
 > You may assume that each input would have exactly one solution, and you may not use the same element twice.

  [LeetCode](https://leetcode.com/problems/two-sum/)

 ```Approach:```

  The key to the problem is that there is ALWAYS only 1 pair of numbers that satisfy the condition of adding together to be the target value.
  
  We can assume that for all the numbers in the list (x1, x2, ... xn) that there exists a pair such that xi + xj = target.
  
  To solve this with a single pass of the list we can change the equation above to xi = target - xj, since we know the target as long as we maintain a record of all previous values in the list we can compare the current value (xi) to it's ONLY pair, if it exists, in record of all previous values (xj).

  To keep a record of the previous values and their indices ***i*** we can use a dictionary. Commonly known as a map in other languages. This allows me to record each previous number in the dictionary alongside the indice as a key value pair (target-number, indice).
  
### 2. Best time to Buy and Sell
  > You are given an array prices where prices\[i] is the price of a given stock on the ith day.
  > 
  > You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.
  > 
  > Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

  [LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

  <!--```Appraoch:```
  
   We always need to know - What is the maxProfit we can make if we sell the stock on i-th day. So, we have to keep track of maxProfit.
   
   There might be a scenario where if stock bought on i-th day is minimum and we sell it on (i + k)th day. So, we also have to keep track of minPurchase as well. -->
 ### 3. Contains Duplicate
  > Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.

  [LeetCode](https://leetcode.com/problems/contains-duplicate/)

 ### 4. Product of Array Except Self
  > Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums\[i].
  > 
  > The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.
  > 
  > You must write an algorithm that runs in O(n) time and without using the division operation.

  [LeetCode](https://leetcode.com/problems/product-of-array-except-self/)

 ### 5. Maximum Subarray
  > Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.
  > 
  > A subarray is a contiguous part of an array.

  [LeetCode](https://leetcode.com/problems/maximum-subarray/)
  
  ```Can use Kadane's Algorithm.```
  
  [Kadane's explanation](https://medium.com/@rsinghal757/kadanes-algorithm-dynamic-programming-how-and-why-does-it-work-3fd8849ed73d)

 ### 6. Maximum product subarray
  > Given an integer array nums, find a contiguous non-empty subarray within the array that has the largest product, and return the product.
  > 
  > A subarray is a contiguous subsequence of the array.

  [LeetCode](https://leetcode.com/problems/maximum-product-subarray/)

  ``` Approach:```
  
  - Variation of Largest Contiguous Sum Subarray Problem
  - Here, we have to deal with negative elements also in the array.
  - Whenever a negative element is multiplied with the current maximum product, it becomes minimum product and vice versa right?
  - So, we will be finding both current maximum as well as minimum product upto every index i.
  - Also, note that whenever we'll encounter the negative element, we will swap the max product and minimum product.
  - Take maximum for every index i

 ### 7. Find Minimum in rotated Sorted Array
  > Suppose an array of length n sorted in ascending order is rotated between 1 and n times. For example, the array nums = \[0,1,2,4,5,6,7] might become:
  > 
  > \[4,5,6,7,0,1,2] if it was rotated 4 times.
  > 
  > \[0,1,2,4,5,6,7] if it was rotated 7 times.
  > 
  > Notice that rotating an array \[a\[0], a\[1], a\[2], ..., a\[n-1]] 1 time results in the array \[a\[n-1], a\[0], a\[1], a\[2], ..., a\[n-2]].
  > 
  > Given the sorted rotated array nums of unique elements, return the minimum element of this array.
  > 
  > Expected time complexity O(log n).

 [LeetCode](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

 ```Approach:```
 
  - Binary search

 ### 8. Search in Rotated Sorted Array
  > There is an integer array nums sorted in ascending order (with distinct values).
  > 
  > Prior to being passed to your function, nums is possibly rotated at an unknown pivot index k (1 <= k < nums.length) such that the resulting array is \[nums\[k], nums\[k+1], ..., nums\[n-1], nums\[0], nums\[1], ..., nums\[k-1]] (0-indexed). For example, \[0,1,2,4,5,6,7] might be rotated at pivot index 3 and become \[4,5,6,7,0,1,2].
  > 
  > Given the array nums after the possible rotation and an integer target, return the index of target if it is in nums, or -1 if it is not in nums.
  > 
  > Expected time complexity O(log n).
 
 [LeetCode](https://leetcode.com/problems/search-in-rotated-sorted-array/)
 
 ```Approach:```
 There are three cases for when we search on the right half of each step.
 1. If target is between mid and right (easiest case, we know it might be in the right half b/c target is greater than mid but less than right)
 2. If target is greater than mid, and left is less than/equal to mid (even though right will be less than mid, we know it's not in the left half as left is smaller than mid)
 3. If target is less than left, and left is less than/equal to mid (left is smaller than mid, we know it's not iin the left half as target is smaller than left)

 ### 9. Triplet Sum equal Zero
  > Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.

[LeetCode](https://leetcode.com/problems/3sum/)


 ### 10. Container with most water
  > You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height\[i]).
  > 
  > Find two lines that together with the x-axis form a container, such that the container contains the most water.
  > 
  > Return the maximum amount of water a container can store.

  ![image](https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question_11.jpg)

  [LeetCode](https://leetcode.com/problems/container-with-most-water/)

  
