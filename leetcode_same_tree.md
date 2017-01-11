title: LeetCode Same Tree
date: 2015-06-21 15:27:09
tags: leetcode
---


# Description

Given two binary trees, write a function to check if they are equal or not.

Two binary trees are considered equal if they are structurally identical and the nodes have the same value.

The original problem is [here](https://leetcode.com/problems/same-tree/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/SameTree.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Same Tree
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
	    bool isSameTree(TreeNode* p, TreeNode* q) {
	        if(p==NULL && q!=NULL)
	        	return false;
	        if(p!=NULL && q==NULL)
	        	return false;
	        if(p == NULL && q == NULL)
	        	return true;
	        if(p->val != q->val)
	        	return false;
	        if(isSameTree(p->left,q->left) && isSameTree(p->right,q->right))
	        	return true;
	        else
	        	return false;
	    }
	};


# Note
To solve the problem, we use depth-first search to search the tree. In the process, recursion is needed. 
