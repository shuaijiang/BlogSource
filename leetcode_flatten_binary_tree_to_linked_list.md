title: LeetCode Flatten Binary Tree To Linked List
date: 2015-07-14 10:20:04
tags: leetcode
---

# Description
Given a binary tree, flatten it to a linked list in-place.

For example,
Given

         1
        / \
       2   5
      / \   \
     3   4   6

The flattened tree should look like:

	   1
	    \
	     2
	      \
	       3
	        \
	         4
	          \
	           5
	            \
	             6

The original problem is [here](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/FlattenBinaryTreeToLinkedList.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Flatten Binary Tree to Linked List 
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
	    void flatten(TreeNode* root) {
	        stack<TreeNode*> myStack;
	        if(root==NULL)
	        	return;
	
	        if(root->right!=NULL)
	        	myStack.push(root->right);
	        if(root->left!=NULL)
	        	myStack.push(root->left);
	        root->left = NULL;
			root->right= NULL; 
	        TreeNode * lastNode = root;
	        while(!myStack.empty()){
	        	TreeNode * node = myStack.top();
	        	myStack.pop();
	        	if(node->right!=NULL)	
	        		myStack.push(node->right);
	        	if(node->left!=NULL)
	        		myStack.push(node->left);
	        	node->left=NULL;
	        	node->right=NULL;
				lastNode->right=node;
	        	lastNode->left =NULL;
	        	
				lastNode = lastNode->right;
	        }
	    }
	};

# Note
In order to flatten the binary tree, we need to traversal the tree by pre-order and put the all child nodes to right of the father node. 
