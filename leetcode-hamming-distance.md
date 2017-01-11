---
title: LeetCode Hamming Distance
date: 2017-01-10 19:28:03
tags: leetcode
---

# Description
The Hamming distance between two integers is the number of positions at which the corresponding bits are different.

Given two integers x and y, calculate the Hamming distance.

Note:
0 ≤ x, y < 2^31.

The original problem is [here](https://leetcode.com/problems/hamming-distance/ "Problem").

<!--more-->

# My Solution
I solve this problem in C++, as below:
```
	class Solution {
		public:
		    int hammingDistance(int x, int y) {
		        int big = x > y ? x : y;
		        int small = x < y ? x : y;
		        int distance = 0;
		        int bigMod, smallMod;
		        while(big > 0) {
		            bigMod = big % 2;
		            smallMod = small % 2;
		            if(bigMod != smallMod) {
		                distance ++;
		            }
		            big = big / 2;
		            small = small / 2;
		        }
		        return distance;
		 }
	};
```
# Note
To solve the problem, convert the integer to binary and compare the every bit. 
