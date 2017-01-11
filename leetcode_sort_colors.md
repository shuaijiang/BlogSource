title: LeetCode Sort Colors
date: 2015-07-12 11:44:44
tags: leetcode
---


# Description
Given an array with n objects colored red, white or blue, sort them so that objects of the same color are adjacent, with the colors in the order red, white and blue.

Here, we will use the integers 0, 1, and 2 to represent the color red, white, and blue respectively.

The original problem is [here](https://leetcode.com/problems/sort-colors/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/SortColors.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Sort Colors 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    void sortColors(vector<int>& nums) {
	        if(nums.size()<=0)
	        	return;
	        
			int c0=0,c1=0,c2=0;
	        for(int i=0;i<nums.size();i++){
	        	if(nums[i]==0)
	        		c0++;
	        	else if(nums[i]==1)
	        		c1++;
	        	else if(nums[i]==2)
	        		c2++;
			}
			for(int i=0;i<nums.size();i++){
				if(i<c0)
					nums[i] = 0;
				else if(i-c0<c1)
					nums[i] = 1;
				else
					nums[i] = 2;
			}
			return;
	    }
	};


# Note
A rather straight forward solution is a two-pass algorithm using counting sort. First, iterate the array counting number of 0's, 1's, and 2's, then overwrite array with total number of 0's, then 1's and followed by 2's.
