title: LeetCode Majority Element 2
date: 2015-07-27 23:32:45
tags: leetcode
---

# Description
Given an integer array of size n, find all elements that appear more than ⌊ n/3 ⌋ times. The algorithm should run in linear time and in O(1) space.

The original problem is [here](https://leetcode.com/problems/majority-element-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/MajorityElement2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Majority Element II 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    vector<int> majorityElement(vector<int>& nums) {
	        int size = nums.size();
	        vector<int> result;
	    	if(size <= 1)
	    		return nums;
	    	if(size == 2){
	    		if(nums[0] != nums[1])
	    			return nums;
	    		else{
	    			result.push_back(nums[0]);
	    			return result;
	    		}
	    	}
	    	sort(nums.begin(),nums.end());
	    	int count = 1;
			for(int i=1;i<size;i++){
	    		if(nums[i] == nums[i-1]){
	    			count++;
	    		}
	    		else{
	    			if(count>size/3)
	    				result.push_back(nums[i-1]);
	    			count = 1;
	    		}
	    	}
	    	if(count > size/3)
	    		result.push_back(nums[size-1]);
	    	return result;
	    }
	};

# Note
To solve this problem, sort the array first. Then, traversal the array, if the  element appears more than [n/3] times, add it to the result.   
