title: LeetCode Find Minimum In Rotated Sorted Array
date: 2015-07-08 11:32:53
tags: leetcode
---


# Description

Suppose a sorted array is rotated at some pivot unknown to you beforehand.

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).

Find the minimum element.

You may assume no duplicate exists in the array.


The original problem is [here](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/FindMinimumInRotatedSortedArray.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*Find Minimum in Rotated Sorted Array
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int findMin(vector<int>& nums) {
	    	if(nums.size()==0)
	    		return 0;
	    	if(nums.size()==1)
	    		return nums[0];
	        for(int i=1;i<nums.size();i++){
	        	if(nums[i-1]>nums[i])
	        		return nums[i];
	        }
	        return nums[0];
	    }
	};

# Note:
Find the number which is smaller than the number before it.
