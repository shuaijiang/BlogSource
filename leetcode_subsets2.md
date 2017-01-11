title: LeetCode Subsets2
date: 2015-07-20 18:21:09
tags: leetcode
---

# Description
Given a collection of integers that might contain duplicates, nums, return all possible subsets.

Note:
Elements in a subset must be in non-descending order.
The solution set must not contain duplicate subsets.
For example,
If nums = [1,2,2], a solution is:

	[
	  [2],
	  [1],
	  [1,2,2],
	  [2,2],
	  [1,2],
	  []
	]

The original problem is [here](https://leetcode.com/problems/subsets-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/Subsets2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*
	*Subsets 2
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	     vector<vector<int>> subsetsWithDup(vector<int>& nums){
	    	vector<vector<int>> result;
	        if(nums.size()<=0)
	        	return result;
	        sort(nums.begin(),nums.end());
	        
	        vector<int> vec;
	        int lastSize = 0;
	        result.push_back(vec);
	        vec.push_back(nums[0]);
	        result.push_back(vec);
	        lastSize = 1;
	        
			for(int i=1;i<nums.size();i++){
				if(nums[i] != nums[i-1]){
					int resultSize = result.size();
					lastSize = resultSize;
					for(int j=0;j<resultSize;j++){
						vector<int> vec = result[j];
						vec.push_back(nums[i]);
						sort(vec.begin(),vec.end());
						result.push_back(vec);
					}
				}
				else{
					int resultSize = result.size();
					for(int j=0;j<lastSize;j++){
						vector<int> vec = result[resultSize - j - 1];
						vec.push_back(nums[i]);
						sort(vec.begin(),vec.end());
						result.push_back(vec);
					}
				}
			}
			return result;
	    }
	};




# Note
To solve the problem, I add one element of the nums to each vector of the result each iterator. If the current number is same to the last one, we just add the current number to the vectors which contain the last number(in other word, the vectors were add to result last iterator).
