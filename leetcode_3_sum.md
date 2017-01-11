title: LeetCode 3 Sum
date: 2015-07-25 13:41:51
tags: leetcode
---

# Description
Given an array S of n integers, are there elements a, b, c in S such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

Note:
Elements in a triplet (a,b,c) must be in non-descending order. (ie, a ≤ b ≤ c)
The solution set must not contain duplicate triplets.
    
	For example, given array S = {-1 0 1 2 -1 -4},

    A solution set is:
    (-1, 0, 1)
    (-1, -1, 2)

The original problem is [here](https://leetcode.com/problems/3sum/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/3Sum.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*3Sum
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
		vector<vector<int>> result;
	    vector<vector<int>> threeSum(vector<int>& nums) {
	        int size = nums.size();
			if(size <= 2)
				return result;
			sort(nums.begin(),nums.end());
			for(int i=0;i<size-2;i++)
			{
				if(i>0 && nums[i]==nums[i-1])
					continue;
				twoSum(nums, i+1,size-1, nums[i]);
			}
			return result;
	    }
	    void twoSum(vector<int> &nums, int start, int end, int target){
	    	vector<int> oneSet;
	    	
	    	while(start<end){
	    		if(nums[start]+nums[end]+target == 0){
	    			oneSet.push_back(target);
					oneSet.push_back(nums[start]);
	    			oneSet.push_back(nums[end]);
	    			result.push_back(oneSet);
	    			oneSet.clear();
	    			while(start<end && nums[start]==nums[start+1]) start++;
	    			while(start<end && nums[end]==nums[end-1]) end--;
	    			start ++;
	    			end --;
	    		}
	    		else if(nums[start]+nums[end]+target < 0)
	    			start ++;
	    		else
	    			end--;
	    	}
			return ;
	    }
	};

# Note
For the problem, first sort the array. Then, for a number A in the array, select two numbers(B and C) from the set after A, which A+B+C=0. When select B and C, we find them from the head and tail of the array.
