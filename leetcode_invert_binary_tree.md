title: LeetCode Invert Binary Tree
date: 2015-06-22 12:22:53
tags: leetcode
---


# Description
nvert a binary tree.

   4
   /   \
  2     7
 / \   / \
1   3 6   9
to
   4
   /   \
  7     2
 / \   / \
9   6 3   1


The original problem is [here](https://leetcode.com/problems/invert-binary-tree/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/InvertBinaryTree.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*
	*Invert Binary Tree
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
	    TreeNode* invertTree(TreeNode* root) {
	    	TreeNode *temp;
	    	if(root == NULL)
	    		return root;
	    	temp = root->left;
	    	root->left  = root->right;
	    	root->right = temp;
	    	
	        root->left  = invertTree(root->left);
	        root->right = invertTree(root->right);
	        
			return root;
	    }
	};


# Note
In the solution, recursion is needed. 
