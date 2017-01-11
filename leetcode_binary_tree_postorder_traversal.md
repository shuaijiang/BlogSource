title: LeetCode Binary Tree Postorder Traversal 
date: 2015-07-13 23:34:06
tags: leetcode
---

# Description
Given a binary tree, return the postorder traversal of its nodes' values.

For example:
Given binary tree {1,#,2,3},

	   1
	    \
	     2
	    /
	   3

return [3,2,1].

The original problem is [here](https://leetcode.com/problems/binary-tree-postorder-traversal/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/BinaryTreePostorderTraversal.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Binary Tree Postorder Traversal 
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
	    vector<int> postorderTraversal(TreeNode* root) {
	        vector<int> vec;
	        stack<TreeNode*> myStack;
	        if(root==NULL)
	        	return vec;
	
	       	myStack.push(root);
	        while(!myStack.empty()){
	        	TreeNode *node = myStack.top();
	        	myStack.pop();
	        	TreeNode *left = node->left;
				TreeNode *right = node->right; 
	        	if(left == NULL && right == NULL){
	        		vec.push_back(node->val);	
	        	}
	        	else{
	        		node->left = NULL;
	        		node->right = NULL;
	        		myStack.push(node);
	        	}
	        	if(right!=NULL)
	        		myStack.push(right);
	        	if(left!=NULL)
					myStack.push(left);
	        }
	        return vec;   
	    }
	};

# Note
To solve the problem, a stack is used. The postorder traversal of the binary tree is left, right and root. So that the order in the stack is root, right and left.
