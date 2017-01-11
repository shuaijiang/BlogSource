title: LeetCode Binary Tree Preorder Traversal
date: 2015-06-29 22:08:38
tags: leetcode
---


# Description
Given a binary tree, return the preorder traversal of its nodes' values.

For example:
Given binary tree {1,#,2,3},
    1
    \
     2
    /
    3
return [1,2,3].

The original problem is [here](https://leetcode.com/problems/binary-tree-preorder-traversal/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/BinaryTreePreorderTraversal.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Binary Tree Preorder Traversal 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stack>
	#include<vector>
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
	    vector<int> preorderTraversal(TreeNode* root) {
	        vector<int> vec;
	        stack<TreeNode*> myStack;
	        TreeNode * node;
	        if(root != NULL)
	        	myStack.push(root);
	        while(!myStack.empty()){
	        	node = myStack.top();
	        	vec.push_back(node->val);
	        	myStack.pop();
	        	if(node->right!=NULL)
	        		myStack.push(node->right);
	        	if(node->left!=NULL)
				myStack.push(node->left);
	        }
	        return vec;
	        
	    }
	};

# Note
A stack is needed for traversal the tree iteratively.
