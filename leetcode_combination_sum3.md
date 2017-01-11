title: LeetCode Combination Sum 3
date: 2015-08-03 17:54:05
tags: leetcode
---

# Description
Find all possible combinations of k numbers that add up to a number n, given that only numbers from 1 to 9 can be used and each combination should be a unique set of numbers.

Ensure that numbers within the set are sorted in ascending order.

Example 1:

	Input: k = 3, n = 7

Output:

	[[1,2,4]]

Example 2:

	Input: k = 3, n = 9

Output:

	[[1,2,6], [1,3,5], [2,3,4]]

The original problem is [here](https://leetcode.com/problems/combination-sum-iii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/CombinationSum3.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Combination Sum
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
		vector<vector<int>> result;
		vector<int> nums;
	    vector<vector<int>> combinationSum3(int k, int n) {       	
			for(int i=1;i<=9;i++)
				nums.push_back(i);
			int size = nums.size();
	        if(size <= 0)
	        	return result;
	        vector<int> oneSet;
			oneCombination(oneSet, 0, k, n);
			return result;
	    }
	    void oneCombination(vector<int> &oneSet, int start, int k, int target) {    	
		    if(oneSet.size() > k)
		    	return;
			if(target < 0)
				return;
			else if(target == 0){
				for(int i=0;i<result.size();i++){
					if(sameSet(result[i], oneSet))
						return;
				}
				if(oneSet.size() == k)
					result.push_back(oneSet);
				return;
			}
			for(int i=start;i < nums.size(); i++){
				int newTarget = target-nums[i];
				oneSet.push_back(nums[i]);
				oneCombination(oneSet, i+1, k, newTarget);
				oneSet.pop_back();
	    	}
	    	return;
	    }
	    bool sameSet(vector<int> set1, vector<int> set2) {
	    	int size1 = set1.size();
			int size2 = set2.size();
			if(size1 != size2)
				return false;
			for(int i=0;i<size1;i++) {
				if(set1[i] != set2[i])
					return false;
			}
			return true;
	    }
	};


# Note
To solve the problem, recursion is used. Similar to Combination Sum and Combination Sum II, but we need to judge the size of each set in the result.
