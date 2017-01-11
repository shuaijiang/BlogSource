title: LeetCode Search In Rotated Sorted Array 2
date: 2015-08-04 12:14:29
tags: leetcode
---

# Description
Follow up for "Search in Rotated Sorted Array":
What if duplicates are allowed?

Would this affect the run-time complexity? How and why?

Write a function to determine if a given target is in the array.

The original problem is [here](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/SearchInRotatedSortedArray2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Search in Rotated Sorted Array II
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<map>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    bool search(vector<int>& nums, int target) {
	    	int size = nums.size();
	    	if(size <= 0)
	    		return false;
			
			sort(nums.begin(),nums.end());
			
			int start, end, middle;
			start = 0; 
			end = size-1;
			
			while(start <= end){
				middle = (start+end) / 2;
				if(nums[middle] == target){
					return true;
				}	
				else if(nums[middle] > target)
					end = middle - 1;
				else
					start = middle + 1;
			}
			return false;
	    }
	};

# Note
To solve the problem, binary search is used.
