title: LeetCode Validate Binary Search Tree
date: 2015-07-27 10:14:53
tags: leetcode
---

# Description
Given a binary tree, determine if it is a valid binary search tree (BST).

Assume a BST is defined as follows:

- The left subtree of a node contains only nodes with keys less than the node's key.

- The right subtree of a node contains only nodes with keys greater than the node's key.

- Both the left and right subtrees must also be binary search trees.

The original problem is [here](https://leetcode.com/problems/validate-binary-search-tree/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ValidateBinarySearchTree.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Validate Binary Search Tree  
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
	    bool isValidBST(TreeNode* root) {
	        if(root==NULL)
	        	return true;
	        vector<int> nums;
	        stack<TreeNode*> myStack;
	        TreeNode *leftNode  = root->left;
	    	TreeNode *rightNode = root->right;
			
			if(rightNode != NULL)
				myStack.push(rightNode);
			
			root->left = root->right = NULL;
			myStack.push(root);
			
			if(leftNode != NULL)
				myStack.push(leftNode);
			
			while(!myStack.empty()){
				TreeNode * node = myStack.top();
				myStack.pop();
				leftNode  = node->left;
				rightNode = node->right;
				if(leftNode==NULL && rightNode==NULL){
					int size = nums.size();
					if(size >=1 && nums[size-1] >= node->val)
						return false;
					else
						nums.push_back(node->val);
				}
					
				else{
					if(rightNode != NULL)
						myStack.push(rightNode);
					
					node->left = node->right = NULL;
					myStack.push(node);
					
					if(leftNode != NULL)
						myStack.push(leftNode);
				}
			}
			return true;	
	    }
	
	};


# Note
To solve the problem, travseral the tree inorder and save the value to the vector. If the new added value is smaller than the last one in the vector, then return false, else return true.
