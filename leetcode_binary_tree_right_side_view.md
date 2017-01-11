title: LeetCode Binary Tree Right Side View
date: 2015-07-09 13:22:20
tags: leetcode
---

# Description

Given a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.

For example:
Given the following binary tree,
   1            <---
 /   \
2     3         <---
 \     \
  5     4       <---
You should return [1, 3, 4].

The original problem is [here](https://leetcode.com/problems/binary-tree-right-side-view/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/BinaryTreeRightSideView.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*Binary Tree Right Side View
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
	    vector<int> rightSideView(TreeNode* root) {
	        vector<int> value;
	        if(root == NULL)
	        	return value;
	        
	        vector<TreeNode*> oneLevel;
	        vector<vector<TreeNode*>> myTree;
	        TreeNode *node;
	
	        oneLevel.push_back(root);
	        myTree.push_back(oneLevel);
	        while(oneLevel.size()>=1){
	        	vector<TreeNode*> nextLevel;
				for(int i=0;i<oneLevel.size();i++)
				{
					node = oneLevel[i];
					if(node->left != NULL)
						nextLevel.push_back(node->left);
					if(node->right != NULL)
						nextLevel.push_back(node->right);
				}
				if(nextLevel.size()>=1)
					myTree.push_back(nextLevel);
				oneLevel = nextLevel;
	        }
			for(int i=0;i<myTree.size();i++){
				vector<TreeNode*> level = myTree[i];
				int size = level.size();
				node = level[size-1];
				value.push_back(node->val);
			}
			return value;
	    }
	};


# Note
To solve the problem, we use breadth-first search to search the tree. We get the all values of final node in one level. 
