title: LeetCode Combination Sum 2
date: 2015-08-03 14:45:35
tags: leetcode
---

# Description
Given a collection of candidate numbers (C) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.

Each number in C may only be used once in the combination.

Note:

- All numbers (including target) will be positive integers.
- Elements in a combination (a1, a2, … , ak) must be in non-descending order. (ie, a1 ≤ a2 ≤ … ≤ ak).
- The solution set must not contain duplicate combinations.

For example, given candidate set 10,1,2,7,6,1,5 and target 8, 
A solution set is: 
[1, 7] 
[1, 2, 5] 
[2, 6] 
[1, 1, 6] 

The original problem is [here](https://leetcode.com/problems/combination-sum-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/CombinationSum2.cpp "Code").
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
	    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {       	
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
				for(int i=0;i<result.size();i++){
					if(sameSet(result[i], oneSet))
						return;
				}
				result.push_back(oneSet);
				return;
			}
			for(int i=start;i < candidates.size(); i++){
				int newTarget = target-candidates[i];
				oneSet.push_back(candidates[i]);
				oneCombination(candidates, oneSet, i+1, newTarget);
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
To solve the problem, recursion is used. We also need to judge whether the reslt has duplicate combinations.
