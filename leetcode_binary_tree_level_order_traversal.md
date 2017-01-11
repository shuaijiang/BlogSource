title: LeetCode Binary Tree Level Order Traversal
date: 2015-06-30 11:22:00
tags: leetcode
---



# Description
Given a binary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).

For example:
Given binary tree {3,9,20,#,#,15,7},
    3
   / \
  9  20
    /  \
   15   7
return its level order traversal as:
[
  [3],
  [9,20],
  [15,7]
]

The original problem is [here](https://leetcode.com/problems/binary-tree-level-order-traversal/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/BinaryTreeLevelOrderTraversal.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Binary Tree Level Order Traversal
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
	    vector<vector<int>> levelOrder(TreeNode* root) {
	        vector<int> vec;
			vector<vector<int>> res;
			TreeNode* node;
	        vector<TreeNode*> currentLevel, nextLevel;
	        if(root==NULL)
	        	return res;
	        if(root!=NULL)
	        	currentLevel.push_back(root);
	        do{
	        	for(int i=0;i<currentLevel.size();i++){
		        	node = currentLevel[i];
		        	vec.push_back(node->val);
		        	if(node->left!=NULL)
		        		nextLevel.push_back(node->left);
		        	if(node->right!=NULL)
						nextLevel.push_back(node->right);
	        	}
	        	res.push_back(vec);
	        	vec.clear();
	        	currentLevel.clear();
	        	currentLevel = nextLevel;
	        	nextLevel.clear();
	        }while(!currentLevel.empty());
	
	        return res;
	    }
	};
	

# Note
To solve the problem, a vector is needed to save tree nodes at one level. 
