title: LeetCode Construct Binary Tree from Inorder and Postorder Traversal
date: 2015-09-15 08:38:09
tags: leetcode
---

# Description
Given inorder and postorder traversal of a tree, construct the binary tree.

Note:
You may assume that duplicates do not exist in the tree.

The original problem is [here](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ConstructBinaryTreeFromInorderAndPostorderTraversal.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Construct Binary Tree from Inorder and Postorder Traversal
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	
	//Definition for a binary tree node.
	 struct TreeNode {
	     int val;
	     TreeNode *left;
	     TreeNode *right;
	     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
	 };
	
	class Solution {
	public:
	    TreeNode* buildTree(vector<int>& inorder, vector<int>& postorder) {
	        int len1 = postorder.size();
	        int len2 = inorder.size();
	        if(len1 != len2)
	        	return NULL;
	        if(len1 <= 0)
	        	return NULL;
	        TreeNode * root = build(inorder, 0, len1-1, postorder, 0, len1-1);
	        return root;
	    }
	    TreeNode* build(vector<int>& inorder, int ni, int nj, vector<int>& postorder, int pi, int pj){
	    	if(pi > pj)
	    		return NULL;
			if(ni > nj)
	    		return NULL;
	    	
			int val = postorder[pj];
			TreeNode *node = new TreeNode(val);
			if(pi == pj){
				return node;
			}
			int pos = ni;
	    	for(int i=ni;i<=nj;i++){
	        	if(inorder[i] == val) {
	        		pos = i;
	        		break;
	        	}
	        }
	        int leftLen  = pos-ni;
	        int rightLen = nj-pos;
	        
	    	node->left  = build(inorder, ni, pos-1, postorder, pi, pi+leftLen-1);
	    	node->right = build(inorder, pos+1, nj, postorder, pj-rightLen, pj-1);
	    	return node;
	    }
	};


# Note
根据后序序列，可以找到根节点，或者子树的根节点；在根据中序序列，可以分别找到左子树和右子树。递归地计算左子树和右子树，直至序列中只有一个节点，即叶子节点，就返回。
