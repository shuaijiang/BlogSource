title: LeetCode Product Of Array Except Self
date: 2015-07-17 23:04:07
tags: leetcode
---

# Description
Given an array of n integers where n > 1, nums, return an array output such that output[i] is equal to the product of all the elements of nums except nums[i].

Solve it without division and in O(n).

For example, given [1,2,3,4], return [24,12,8,6].

The original problem is [here](https://leetcode.com/problems/product-of-array-except-self/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ProductOfArrayExceptSelf.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Permutations 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    vector<int> productExceptSelf(vector<int>& nums) {
	        vector<int> result;
	        int size = nums.size();
	        if(size <= 1){
	        	result.push_back(0);
	        	return result;
	        }
			vector<int> product1, product2;
			
			product1.push_back(nums[0]);
			for(int i=1;i<size;i++){
				int product = nums[i] * product1[i-1];
				product1.push_back(product);
			}
			
			product2 = product1;
			product2[size-1] = nums[size-1];
			for(int i=size-2;i>=0;i--){
				int product = nums[i]  * product2[i+1];
				product2[i] = product;
			}
					
	        for(int i=0;i<size;i++){
	        	int product = 0;
	        	if(i==0)
	        		product = product2[i+1];
	        	else if(i==size-1)
	        		product = product1[i-1];
	        	else
					product = product1[i-1] * product2[i+1];
	        	
				result.push_back(product);
	        }
	        return result;
	    }
	};

# Note
I need two extra array, one array to save the products of the current number and the numbers before it, the other one to save the products of the current number and the numbers afer it.
