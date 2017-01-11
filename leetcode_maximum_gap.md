title: LeetCode Maximum Gap
date: 2015-08-06 21:49:22
tags: leetcode
---

# Description
Given an unsorted array, find the maximum difference between the successive elements in its sorted form.

Try to solve it in linear time/space.

Return 0 if the array contains less than 2 elements.

You may assume all elements in the array are non-negative integers and fit in the 32-bit signed integer range.

The original problem is [here](https://leetcode.com/problems/maximum-gap/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/MaximumGap.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Maximum Gap
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int maximumGap(vector<int>& nums) {
			int size = nums.size();
			if(size < 2)
				return 0;
			sort(nums.begin(),nums.end());
			int maxGap = 0;
			for(int i=1;i<size;i++){
				if(nums[i]-nums[i-1] > maxGap)
					maxGap = nums[i]-nums[i-1];
			}
			return maxGap;
	    }
	};


# Note
To solve the problem, first sort the array, and then find the maximum gap. 
