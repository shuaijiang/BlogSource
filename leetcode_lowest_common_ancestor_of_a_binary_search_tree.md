title: LeetCode Lowest Common Ancestor of a Binary Search Tree
date: 2015-07-14 23:19:28
tags: leetcode
---

# Description
Given a binary search tree (BST), find the lowest common ancestor (LCA) of two given nodes in the BST.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes v and w as the lowest node in T that has both v and w as descendants (where we allow a node to be a descendant of itself).”

	        _______6______
	       /              \
	    ___2__          ___8__
	   /      \        /      \
	   0      _4       7       9
	         /  \
	         3   5
For example, the lowest common ancestor (LCA) of nodes 2 and 8 is 6. Another example is LCA of nodes 2 and 4 is 2, since a node can be a descendant of itself according to the LCA definition.

The original problem is [here](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/LowestCommonAncestorOfABinarySearchTree.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Lowest Common Ancestor of a Binary Search Tree
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<math>
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
	    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
	        int pValue = p->val;
	        int qValue = q->val;
	        int rValue = root->val;
			if(min(pValue,qValue)<=rValue && max(pValue,qValue)>=rValue)
				return root;
			else if(min(pValue,qValue)>=rValue)
				return lowestCommonAncestor(root->right,p,q);
			else if(max(pValue,qValue)<=rValue)
				return lowestCommonAncestor(root->left,p,q);
	    }
	};

# Note
Because the tree is binary search tree, for the two nodes, if one value is less than the root, the other is larger than the root, then the root is the result. If the two values are all smaller than the root, we go on to find the result from the left of the root. If the two values are all larger than the root, we go on to find the result from the right of the root. 
