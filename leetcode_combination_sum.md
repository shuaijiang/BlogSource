title: LeetCode Combination Sum
date: 2015-08-03 14:31:31
tags: leetcode
---

# Description
Given a set of candidate numbers (C) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.

The same repeated number may be chosen from C unlimited number of times.

Note:

- All numbers (including target) will be positive integers.
- Elements in a combination (a1, a2, … , ak) must be in non-descending order. (ie, a1 ≤ a2 ≤ … ≤ ak).
- The solution set must not contain duplicate combinations.

For example, given candidate set 2,3,6,7 and target 7, 
A solution set is: 
[7] 
[2, 2, 3] 

The original problem is [here](https://leetcode.com/problems/combination-sum/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/CombinationSum.cpp "Code").
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
	    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {       	
		    int size = candidates.size();
	        if(size <= 0)
	        	return result;
	        vector<int> oneSet;
			sort(candidates.begin(),candidates.end());
			oneCombination(candidates, oneSet, 0, target);
			return result;
	    }
	    void oneCombination(vector<int>&candidates, vector<int> &oneSet, int start, int target) {    	
		    if(target < 0)
				return;
			else if(target == 0){
				result.push_back(oneSet);
				return;
			}
			for(int i=start;i < candidates.size(); i++){
				int newTarget = target-candidates[i];
				oneSet.push_back(candidates[i]);
				oneCombination(candidates, oneSet, i, newTarget);
				oneSet.pop_back();
	    	}
	    	return;
	    }
	};


# Note
To solve the problem, recursion is used.
