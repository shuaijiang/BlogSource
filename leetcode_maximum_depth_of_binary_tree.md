title: LeetCode Maximum Depth of Binary Tree
date: 2015-06-26 09:44:05
tags: leetcode
---

# Description
Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

The original problem is [here](https://leetcode.com/problems/maximum-depth-of-binary-tree/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/MaximumDepthOfBinaryTree.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*
	*Maximum Depth of Binary Tree
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
	    int maxDepth(TreeNode* root) {
	    	if(root==NULL)
	    		return 0;
	    	if(root->left!=NULL && root->right==NULL)
	    		return 1+maxDepth(root->left);
	    	if(root->left==NULL && root->right!=NULL)
	    		return 1+maxDepth(root->right);
	    	return max(1+maxDepth(root->left),1+maxDepth(root->right));
	    }
	};


# Note
In the solution, recursion is needed.
