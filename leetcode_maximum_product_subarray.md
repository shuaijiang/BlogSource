title: LeetCode Maximum Product Subarray
date: 2015-08-02 13:44:16
tags: leetcode
---


# Description
Find the contiguous subarray within an array (containing at least one number) which has the largest product.

For example, given the array [2,3,-2,4],
the contiguous subarray [2,3] has the largest product = 6.

The original problem is [here](https://leetcode.com/problems/maximum-product-subarray/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/MaximumProductSubarray.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Maximum Product Subarray 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int maxProduct(vector<int>& nums) {
	        int size = nums.size();
	        if(size <= 0)
	        	return 0;
			if(size == 1)
	        	return nums[0];
	        int maxNum = nums[0];
	        int minNum = nums[0];
	        int maxRes = nums[0];
	        for(int i=1;i<size;i++){
	        	int num1 = nums[i] * maxNum;
	        	int num2 = nums[i] * minNum;
				maxNum = max(max(num1,num2),nums[i]);
				minNum = min(min(num1,num2),nums[i]);
				maxRes = max(maxRes, maxNum);
	        }
	        return maxRes;
	    }
	};

# Note
To solve the problem, during traversal the array, save the maxNum and minNum. we need compute the product num1 of maxNum and the current num. If num1 is smaller than the current num, then set the current num to maxNum. It is similar to the minNum. 
