title: LeetCode Subsets
date: 2015-07-20 14:44:01
tags: leetcode
---


# Description
Given a set of distinct integers, nums, return all possible subsets.

Note:
Elements in a subset must be in non-descending order.
The solution set must not contain duplicate subsets.
For example,
If nums = [1,2,3], a solution is:
	
	[
	  [3],
	  [1],
	  [2],
	  [1,2,3],
	  [1,3],
	  [2,3],
	  [1,2],
	  []
	]

The original problem is [here](https://leetcode.com/problems/subsets/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/Subsets.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*
	*Subsets 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    vector<vector<int>> subsets(vector<int>& nums) {
	    	vector<vector<int>> result;
	        if(nums.size()<=0)
	        	return result;
	        vector<int> vec;
	        result.push_back(vec);
			for(int i=0;i<nums.size();i++){
				int resultSize = result.size();
				for(int j=0;j<resultSize;j++){
					vector<int> vec = result[j];
					vec.push_back(nums[i]);
					sort(vec.begin(),vec.end());
					result.push_back(vec);
				}
			}
			return result;
	    }
	};



# Note
To solve the problem, I add one element of the nums to each vector of the result each iterator.
