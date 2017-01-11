title: LeetCode Kth Smallest Element In A BST
date: 2015-07-13 11:15:15
tags: leetcode
---

# Description
Given a binary search tree, write a function kthSmallest to find the kth smallest element in it.

Note: 
You may assume k is always valid, 1 ≤ k ≤ BST's total elements.

The original problem is [here](https://leetcode.com/problems/kth-smallest-element-in-a-bst/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/KthSmallestElementInABST.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Kth Smallest Element in a BST 
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
	    int kthSmallest(TreeNode* root, int k) {
	        stack<TreeNode*> myStack;
	        vector<int> result;
	        if(root==NULL)
	        	return 0;
	        myStack.push(root);
	        
	        while(!myStack.empty()){
	        	TreeNode * node = myStack.top();
	        	myStack.pop();
	        	if(node->left == NULL && node->right == NULL)
	        		result.push_back(node->val);
	        	else{
	        		if(node->right != NULL)
	        			myStack.push(node->right);
	        		TreeNode *left = node->left;
	        		node->left = NULL;
	        		node->right = NULL;
	        		myStack.push(node);
	        		if(left != NULL)
	        			myStack.push(left);				   			
	        	}
				if(result.size()==k)
					return result[k-1];
	        }
	    }
	};


# Note
To solve the problem, I traversal the BST use a stack, and pop the stack from samll element to large. Finally, return the kth smallest element.
