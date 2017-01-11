title: LeetCode Symmetric Tree
date: 2015-06-22 11:10:41
tags: leetcode 
---



# Description

Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

For example, this binary tree is symmetric:

1
   /  \
   2    2
 / \   / \
3  4   4  3
But the following is not:
    1
   / \
  2   2
   \    \
   3     3


The original problem is [here](https://leetcode.com/problems/symmetric-tree/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/SymmetricTree.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*
	*Symmetric Tree
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
	    bool isSymmetric(TreeNode* root) {
	    	if(root == NULL)
	    		return true;
	    	return isSym(root->left,root->right);
	    }
	    bool isSym(TreeNode *p, TreeNode *q){
	    	if(p==NULL && q==NULL)
	    		return true; 
	    	if(p==NULL && q!= NULL)
	    		return false;
	    	if(p!=NULL && q==NULL)
	    		return false;
	    	if(p->val != q->val)
	    		return false;
	    	if(isSym(p->left,q->right) && isSym(p->right,q->left)){
	    		return true;
	    	}
	    	return false;
	    }
	};


# Note
This problem is similar to [Same Tree](https://leetcode.com/problems/same-tree/ "Problem"). In the process, recursion is needed. 
