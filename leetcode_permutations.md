title: LeetCode Permutations
date: 2015-07-17 22:00:28
tags: leetcode
---

# Description
Given a collection of numbers, return all possible permutations.

For example,
[1,2,3] have the following permutations:

[1,2,3], [1,3,2], [2,1,3], [2,3,1], [3,1,2], and [3,2,1].

The original problem is [here](https://leetcode.com/problems/permutations/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/Permutations.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Permutations 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<math.h>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    vector<vector<int>> permute(vector<int>& nums) {
	        vector<vector<int>> result;
			if(nums.size() <= 0)
				return result;
	        findResult(nums, 0, result);
	        return result;
	    }
	    void findResult(vector<int>& nums, int i, vector<vector<int>> &result){
	    	int size = nums.size();
			if(i == size-1){
				result.push_back(nums);
				return;
			}
			for(int j=i;j<nums.size();j++){
	    		int temp = nums[i];
				nums[i] = nums[j];
				nums[j] = temp;
				
				findResult(nums, i+1, result);
				
				temp = nums[i];
				nums[i] = nums[j];
				nums[j] = temp;
	    	}
	    }
	};

# Note
To solve the problem, recursion is needed.  And, we need replace the current number with the numbers after the current. 
