title: LeetCode Minimum Depth of Binary Tree
date: 2015-06-26 09:32:20
tags: leetcode
---



# Description
Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

The original problem is [here](https://leetcode.com/problems/minimum-depth-of-binary-tree/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/MinimumDepthOfBinaryTree.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*
	*Minimum Depth of Binary Tree
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
	    int minDepth(TreeNode* root) {
	    	if(root==NULL)
	    		return 0;
	    	if(root->left!=NULL && root->right==NULL)
	    		return 1+minDepth(root->left);
	    	if(root->left==NULL && root->right!=NULL)
	    		return 1+minDepth(root->right);
	    	
	    	return min(1+minDepth(root->left),1+minDepth(root->right));
	    }
	};


# Note
In the solution, recursion is needed.
