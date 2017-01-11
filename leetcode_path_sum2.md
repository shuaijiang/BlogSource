title: LeetCode Path Sum2
date: 2015-07-24 18:20:17
tags: leetcode
---


# Description
Given a binary tree and a sum, find all root-to-leaf paths where each path's sum equals the given sum.

For example:
Given the below binary tree and sum = 22,

              5
             / \
            4   8
           /   / \
          11  13  4
         /  \    / \
        7    2  5   1
return

	[
	   [5,4,11,2],
	   [5,8,4,5]
	]

The original problem is [here](https://leetcode.com/problems/path-sum-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/PathSum2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Path Sum II 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stack>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
		vector<vector<int>> result;
	    vector< vector<int> > pathSum(TreeNode* root, int sum) {
	    	if(root == NULL)
	    		return result;
	    	vector<int> onePath;
			sumNum(root,onePath,0,sum);
			return result;
	    }
	    void sumNum(TreeNode * root, vector<int> onePath, int oneSum, int sum){
	    	if(root == NULL)
	    		return;
	    	oneSum +=  root->val;
	    	onePath.push_back(root->val);
	    	if(root->left == NULL && root->right == NULL){
	    		if(oneSum == sum)
	    			result.push_back(onePath);
	    		else
	    			return;
	    	}
	    	sumNum(root->left, onePath, oneSum, sum);
			sumNum(root->right, onePath, oneSum, sum);
	    }
	};



# Note
This problem is similar to "path sum". In the solution, recursion is needed. During these steps, we need compute the sum of all the values in the path and save the values in a vector. If the sum of the path is equal to the given sum, we push the vector to the result.
