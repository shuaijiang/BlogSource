title: LeetCode First Missing Positive
date: 2015-07-28 12:12:49
tags: leetcode
---

# Description
Given an unsorted integer array, find the first missing positive integer.

For example,
Given [1,2,0] return 3,
and [3,4,-1,1] return 2.

Your algorithm should run in O(n) time and uses constant space.

The original problem is [here](https://leetcode.com/problems/first-missing-positive/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/FirstMissingPositive.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*
	*First Missing Positive 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<map>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int firstMissingPositive(vector<int>& nums) {
	        int size = nums.size();
	        bool positive = false;
			sort(nums.begin(),nums.end());
	        for(int i=0;i<size;i++){
				if(positive){
					if(nums[i]-nums[i-1] > 1)
						return nums[i-1] + 1;
				}
				else{
					if(nums[i]>0)
						positive = true;
					if(nums[i]>1)
						return 1;
				}
			}
			if(positive)
				return nums[size-1]+1;
			return 1;
	    }
	};


# Note
In the solution, first sort the vector. Then, tranversal the vector and find the positive part, and take the first missing positive.
