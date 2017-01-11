title: LeetCode Binary Tree Zigzag Level Order Traversal
date: 2015-07-14 09:23:16
tags: leetcode
---


# Description
Given a binary tree, return the zigzag level order traversal of its nodes' values. (ie, from left to right, then right to left for the next level and alternate between).

For example:
Given binary tree {3,9,20,#,#,15,7},

	    3
	   / \
	  9  20
	    /  \
	   15   7

return its zigzag level order traversal as:

	[
	  [3],
	  [20,9],
	  [15,7]
	]

The original problem is [here](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/BinaryTreeZigzagLevelOrderTraversal.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Binary Tree Zigzag Level Order Traversal
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
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
	    vector<vector<int>> zigzagLevelOrder(TreeNode* root) {
	        vector<vector<int>> result;
	        vector<TreeNode*> currLevel, nextLevel;
	        if(root==NULL)
	        	return result;
	        currLevel.push_back(root);
	        for(int count=0;currLevel.size()>0;count++){
	        	vector<int> vec;
			    for(int i=currLevel.size()-1;i>=0;i--){
					TreeNode * node = currLevel[i];
		        	vec.push_back(node->val);
		        	if(count%2==0){
		        		if(node->left)
							nextLevel.push_back(node->left);
						if(node->right)
							nextLevel.push_back(node->right);
		        	}
		        	else{
						if(node->right)
							nextLevel.push_back(node->right);
						if(node->left)
							nextLevel.push_back(node->left);
		        	}
		        }
				result.push_back(vec);
		        currLevel = nextLevel;
		        nextLevel.clear();
	        }
			return result; 
	    }
	};

# Note
when traversal the binary tree, use a vector to save the current level nodes and use a vector to save the next level nodes. In order to traversal the tree by zigzag, if the level number can be modulus by 2, traversal the level nodes from left to right, else from right to left.
