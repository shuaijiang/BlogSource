title: LeetCode Number of 1 Bits
date: 2015-04-03 22:11:32
tags: leetcode
---


# Description
Write a function that takes an unsigned integer and returns the number of ’1' bits it has (also known as the Hamming weight).

For example, the 32-bit integer ’11' has binary representation 00000000000000000000000000001011, so the function should return 3.

The original problem is [here](https://leetcode.com/problems/number-of-1-bits/ "Problem").

My code is [here](https://github.com/shuaijiang/LeetCode/blob/master/Numberof1Bits.cpp "Code").

<!--more-->

# My Solution
I solve this problem in C++, as below:

	
	/*
	*Number of 1 Bits
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	class Solution {
	public:
	    int hammingWeight(uint32_t n) {
	        int bitNum = 0;
	        
	        while(n > 1)
	        {
	        	if(n % 2 == 1)
	        		bitNum ++;
	        	
				n = n/2;
	        }
	        if(n%2 == 1)
	        	bitNum ++;
	        return bitNum;
	    }
	};

# Note
It is similar to convert decimal to binary.
