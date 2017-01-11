title: LeetCode Missing Number
date: 2015-08-26 10:44:27
tags: leetcode
---

# Description
Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.

For example,
Given nums = [0, 1, 3] return 2.

Note:
Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity?


The original problem is [here](https://leetcode.com/problems/missing-number/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/MissingNumber.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Missing Number 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int missingNumber(vector<int>& nums) {
	        int size = nums.size();
	        int sum = size * (1 + size) / 2;
	        int total = 0;
	        for(int i=0;i<size;i++){
	        	total += nums[i];
	        }
	        return sum-total;
	    }
	};

# Note
To solve the problem, first comput the sum of the array 0...n with the missing number. Then add all the number to total, we can get the missing number by sum-total.
