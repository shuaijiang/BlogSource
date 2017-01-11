title: LeetCode Path Sum
date: 2015-06-26 14:10:10
tags: leetcode
---



# Description
Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

For example:
Given the below binary tree and sum = 22,
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1
return true, as there exist a root-to-leaf path 5->4->11->2 which sum is 22.

The original problem is [here](https://leetcode.com/problems/path-sum/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/PathSum.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*
	* Path Sum
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<math.h>
	#include<stdlib.h>
	using namespace std;
	
	/**
	 * Definition for a binary tree node.
	 * struct TreeNode {
	 *     int val;
	 *     TreeNode *left;
	 *     TreeNode *right;
	 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
	 * };
	 */
	
	class Solution {
	public:
	    bool hasPathSum(TreeNode* root, int sum) {
	    	if(root == NULL)
	    		return false;
			return 	sumNum(root,0,sum);
	    }
	    bool sumNum(TreeNode * root, int val,int sum){
	    	if(root == NULL)
	    		return false;    
	    	val = val + root->val;
	    	if(root->left == NULL && root->right == NULL){
	    		if(val == sum)
	    			return true;
	    		else
	    			return false;
	    	}
	    	return (sumNum(root->left,val,sum) || sumNum(root->right,val,sum));
	    }
	};



# Note
In the solution, recursion is needed. During these steps, we need compute the sum of all the values in the path.
