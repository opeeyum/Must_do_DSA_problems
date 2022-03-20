## Must do bitwise manipulation question's

### Why bit manipulation?
 Bit manipulation, in some cases, can obviate or reduce the need to loop over a data structure and can give many-fold speed ups, as bit manipulations are processed in parallel, but the code can become more difficult to write and maintain.

### 1. **Write a function that takes an unsigned integer and returns the number of '1' bits it has.**
  > Approach:

   We can perform a bitwise AND with the number and shifitng the right most bit (LSB) to null.
   And we can repeat this until given number becomes Zero.
     
### 2. **Given two integers a and b, return the sum of the two integers without using any arithmetic operations.**
  > Approach:

   Let's try this 3 + 2 = 5 , the carry will be with in the brackets i.e "()"
  ```
    3 => 011 
    2 => 010
        _____
        1(1)01
  ```
  Here we will forward the carry at the second bit to get the result.
  So which bitwise operator can do this ? 
  A simple observation says that XOR can do that, but it just falls short in dealing with the carry properly, 
  but correctly adds when there is no need to deal with carry.
  For Eg:
 ```
  1   =>  001 
  2   =>  010 
  1^2 =>  011 (2+1 = 3)
  ```
  So now when we have carry, to deal with, we can see the result as :
  ```
  3   => 011 
  2   => 010 
  3^2 => 001 
  ````
  Here we can see XOR just fell short with the carry generated at the second bit.
  So how can we find the carry ? 
  The carry is generated when both the bits are set, i.e (1,1) will generate carry, 
  but (0,1 or 1,0 or 0,0) won't generate a carry, so which bitwise operator can do that ? 
  **AND** gate ofcourse.

  To find the carry we can do:
  ```
  3    =>  011 
  2    =>  010 
  3&2  =>  010
  ```
  Now we need to add it to the previous value we generated i.e ( 3 ^ 2), 
  but the carry **should be added to the left bit** of the one which genereated it.
  so we left shift it by one so that it gets added at the right spot.

  Hence (3&2)<<1 => 100
  so we can now do
  ```
  3^2         =>  001 
  (3&2)<<1    =>  100
  ```
  Now xor them, which will give 101(5) , we can continue this until the carry becomes zero.
### 3. Given an integer n, return an array ans of length n + 1 such that for each i (0 <= i <= n), ans[i] is the number of 1's in the binary representation of i.
  ```
  Input: n = 5
  Output: [0,1,1,2,1,2]
  Explanation:
  0 --> 0
  1 --> 1
  2 --> 10
  3 --> 11
  4 --> 100
  5 --> 101
  ```
 > Approach:

  Let say we have X and Y, such a way that,
  ```
  X/2 = Y
  ```
 then number of set bits in X - Number of set bit in Y <= 1
 for example,
 ```
 X = 7
 then, 
 y = 7 / 2 = 3;

 7 -> 1 1 1 number of set bit are 3
 3 -> 0 1 1 number of set bit are 2

 there set bit difference is 3 - 2 <= 1
 ```
 Another example,
 ```
 X = 12
 then,
 y = 12 / 2 = 6;

 12 -> 1100 number of set bit are 2
 6 -> 0110 number of set bit are 2

 there set bit difference is 2 - 2 <= 1
 ```
 There can be 2 cases, whether X is Odd or Even:-

 if X is ODD then, the Least Significant Bit (LSB) will always be set and dividing by 2 means right shifting the number by 1 bit.
 So, if last bit is set then with right shift of 1 we will loose 1 at LSB.
 Therefore the new number Y has 1 set bit less than in compare to X.
 
 But if X is Even then, LSB will be equal to 0, therefore even we do right shift of 1 bit only 0 at LSB will be lost.
 
 - So When we have X has Even, number of set bit in X = number of set bit in Y.
 - And, when X is ODD number of set bit in X = 1 + no of set bit in Y.

 Therefore, for t\[i] number of set bit(s) will equal to t\[i/2] + i%2;
 
### 4. Given an array nums containing n distinct numbers in the range \[0, n], return the only number in the range that is missing from the array.
 > Approach:
 
 The basic idea is to use XOR operation. 
 
 We all know that a^b^b =a, which means two xor operations with the same number will eliminate the number and reveal the original number.
 
 Apply XOR operation to both the index and value of the array. 
 
 In a complete array with no missing numbers, the index and value should be perfectly corresponding (nums\[index] = index), so in a missing array, what left  finally is the missing number.

 
