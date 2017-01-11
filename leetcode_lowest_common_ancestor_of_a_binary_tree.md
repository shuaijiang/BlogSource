title: LeetCode Lowest Common Ancestor Of A Binary Tree
date: 2015-07-27 13:41:55
tags: leetcode
---


# Description
Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes v and w as the lowest node in T that has both v and w as descendants (where we allow a node to be a descendant of itself).”

			 _______3______
			/              \
		 ___5__          ___1__
		/      \        /      \
		6      _2       0       8
			  /  \
			  7   4

For example, the lowest common ancestor (LCA) of nodes 5 and 1 is 3. Another example is LCA of nodes 5 and 4 is 5, since a node can be a descendant of itself according to the LCA definition.

The original problem is [here](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/LowestCommonAncestorOfABinaryTree.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Lowest Common Ancestor of a Binary Tree
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stack>
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
	      if (root == NULL) return NULL;
	         if (root == p || root == q) return root;
	         TreeNode *L = lowestCommonAncestor(root->left, p, q);
	         TreeNode *R = lowestCommonAncestor(root->right, p, q);
	         if (L && R) return root;
	         return L ? L : R;
	    }
	};


# Note
To solve the problem, recursion is needed.
