title: LeetCode Search Insert Position
date: 2015-07-07 22:52:12
tags: leetcode
---



# Description
Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

Here are few examples.
[1,3,5,6], 5 → 2
[1,3,5,6], 2 → 1
[1,3,5,6], 7 → 4
[1,3,5,6], 0 → 0

The original problem is [here](https://leetcode.com/problems/search-insert-position/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/SearchInsertPosition.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	
	/*
	*Search Insert Position
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	
	#include<iostream>
	#include<vector>
	#include <unordered_set>
	#include<string.h>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int searchInsert(vector<int>& nums, int target) {
			if(nums.size()<=0)
	        	return 0;
	        int size = nums.size();
			for(int i=0;i<nums.size();i++){
				if(target <= nums[i])
					return i;
			}
			return size;
	    }
	};


# Note
Just traversal the vector, and return the index of first number which is equal or larger than the target number.
