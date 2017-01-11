title: LeetCode Combinations
date: 2015-07-20 09:03:38
tags: leetcode
---


# Description
Given two integers n and k, return all possible combinations of k numbers out of 1 ... n.

For example,
If n = 4 and k = 2, a solution is:

	[
	  [2,4],
	  [3,4],
	  [2,3],
	  [1,2],
	  [1,3],
	  [1,4],
	]

The original problem is [here](https://leetcode.com/problems/combinations/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/Combinations.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Combinations   
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
		vector<vector<int>> result;
	    vector<vector<int>> combine(int n, int k) {
	        if(k<=0)
	        	return result;
	        vector<int> nums;
	        vector<int> res;
	        for(int i=1;i<=n;i++)
	        	nums.push_back(i);
	        getCombine(nums,res,0,k);
	        return result;
	    }
	    void getCombine(vector<int> &nums, vector<int> res, int start, int k){
	    	if(k == 1){
	    		for(int i=start;i<nums.size();i++){
	    			res.push_back(nums[i]);
	    			result.push_back(res);
	    			res.pop_back();
	    		}
	    	}
	    	for(int i=start;i<nums.size();i++){
	    		res.push_back(nums[i]);
	    		getCombine(nums,res,i+1,k-1);
	    		res.pop_back();
	    	}
	    }
	}; 



# Note
To solve this problem, recursion is needed. 
