title: LeetCode Binary Search Tree Iterator
date: 2015-07-14 10:58:12
tags: leetcode
---

# Description
Implement an iterator over a binary search tree (BST). Your iterator will be initialized with the root node of a BST.

Calling next() will return the next smallest number in the BST.

Note: next() and hasNext() should run in average O(1) time and uses O(h) memory, where h is the height of the tree.

The original problem is [here](https://leetcode.com/problems/binary-search-tree-iterator/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/BinarySearchTreeIterator.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Binary Search Tree Iterator 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stack>
	#include<stdlib.h>
	using namespace std;
	
	/**
	 * Definition for binary tree
	 * struct TreeNode {
	 *     int val;
	 *     TreeNode *left;
	 *     TreeNode *right;
	 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
	 * };
	 */
	class BSTIterator {
	public:
		int nextMin = 0;
		stack<TreeNode*> myStack;
	    BSTIterator(TreeNode *root) {
	        while(root!=NULL){
	        	myStack.push(root);
	        	root=root->left;
	        }
	    }
	
	    /** @return whether we have a next smallest number */
	    bool hasNext() {
	    	if(!myStack.empty()){
	    		TreeNode * node = myStack.top();
	    		myStack.pop();
				nextMin = node->val;
					
				node = node->right;
				while(node){
					myStack.push(node);
					node=node->left;
				}
				
	    		return true;
	    	}
			return false;
	    }
	
	    /** @return the next smallest number */
	    int next() {
			return nextMin;
	    }
	};
	
	/**
	 * Your BSTIterator will be called like this:
	 * BSTIterator i = BSTIterator(root);
	 * while (i.hasNext()) cout << i.next();
	 */

# Note
To get the next smallest value in the binary tree, is similar to traversal the tree by in-order. 
