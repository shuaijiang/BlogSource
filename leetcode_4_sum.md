title: LeetCode 4 Sum
date: 2015-07-26 11:02:23
tags: leetcode
---

# Description
Given an array S of n integers, are there elements a, b, c, and d in S such that a + b + c + d = target? Find all unique quadruplets in the array which gives the sum of target.

Note:
Elements in a quadruplet (a,b,c,d) must be in non-descending order. (ie, a ≤ b ≤ c ≤ d)
The solution set must not contain duplicate quadruplets.

    For example, given array S = {1 0 -1 0 -2 2}, and target = 0.

    A solution set is:
    (-1,  0, 0, 1)
    (-2, -1, 1, 2)
    (-2,  0, 0, 2)

The original problem is [here](https://leetcode.com/problems/4sum/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/4Sum.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*4Sum
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
	    vector<vector<int>> fourSum(vector<int>& nums, int target) {
	        int size = nums.size();
			if(size <= 3)
				return result;
			sort(nums.begin(),nums.end());
			for(int i=0;i<size-3;i++)
			{
				if(i>0 && nums[i]==nums[i-1] )
					continue;
				for(int j=i+1;j<size-2;j++){
					if(j>i+1 && nums[j]==nums[j-1] )
						continue;
					twoSum(nums, j+1, size-1, nums[i], nums[j], target);
				}
			}
			return result;
	    }
	    void twoSum(vector<int> &nums, int start, int end, int num1, int num2, int target){
	    	vector<int> oneSet;
	    	
	    	while(start<end){
	    		if(nums[start]+nums[end] + num1 + num2 == target){
	    			oneSet.push_back(num1);
	    			oneSet.push_back(num2);
					oneSet.push_back(nums[start]);
	    			oneSet.push_back(nums[end]);
	    			result.push_back(oneSet);
	    			oneSet.clear();
	    			while(start<end && nums[start]==nums[start+1]) start++;
	    			while(start<end && nums[end]==nums[end-1]) end--;
	    			start ++;
	    			end --;
	    		}
	    		else if(nums[start]+nums[end] + num1 + num2 < target)
	    			start ++;
	    		else
	    			end--;
	    	}
			return ;
	    }
	};

# Note
For the problem, first sort the array. Then, for a number A in the array,  abd next number B, select two numbers(C and D) from the set after A and B, which A+B+C+D=target. When select C and D, we find them from the head and tail of the array.
