title: LeetCode Binary Tree Level Order Traversal2
date: 2015-06-30 13:13:58
tags: leetcode
---

# Description
Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).

For example:
Given binary tree {3,9,20,#,#,15,7},
    3
   / \
  9  20
    /  \
   15   7
return its bottom-up level order traversal as:
[
  [15,7],
  [9,20],
  [3]
]

The original problem is [here](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/BinaryTreeLevelOrderTraversal2.cpp "Code").
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
	    vector<vector<int>> levelOrderBottom(TreeNode* root) {
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
			
			int size = res.size()-1;
			for(int i=0;i<=size/2;i++){
				vec = res[i];
				res[i] = res[size-i];
				res[size-i] = vec;
			}
	        return res;
	    }
	};
	

# Note
The problem is almost the same to the "Binary Tree Level Order Traversal", just reverse the final result. 
