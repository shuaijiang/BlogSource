title: LeetCode Binary Tree Inorder Traversal
date: 2015-07-10 09:41:18
tags: leetcode
---

# Description
Given a binary tree, return the inorder traversal of its nodes' values.

For example:
Given binary tree {1,#,2,3},
   1
    \
     2
    /
   3
return [1,3,2].

The original problem is [here](https://leetcode.com/problems/binary-tree-inorder-traversal/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/BinaryTreeInorderTraversal.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*
	*Binary Tree Inorder Traversal  
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
	    vector<int> inorderTraversal(TreeNode* root) {
	        stack<TreeNode*> myStack;
	        vector<int> result;
	        if(root == NULL)
	        	return result;
	        myStack.push(root);
	        while(!myStack.empty()){
	        	TreeNode * node = myStack.top();
	        	myStack.pop();
				if(node->left == NULL && node->right == NULL)
					result.push_back(node->val);
				else{
					TreeNode * left = NULL;
					if(node->right != NULL){
						myStack.push(node->right);
						node->right = NULL;
					}
					if(node->left != NULL){
						left = node->left;
						node->left = NULL; 
					}
					myStack.push(node);
					if(left != NULL)
						myStack.push(left);
				}
	        }
	        return result;
	    }
	};


# Note
To solve the problem, I use a stack to save the node of the tree. 
