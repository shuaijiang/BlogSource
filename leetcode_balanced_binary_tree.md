title: LeetCode: Balanced Binary Tree
date: 2015-04-01 21:37:25
tags: leetcode
---

#Description
Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

The original problem is [here](https://leetcode.com/problems/balanced-binary-tree/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/BalancedBinaryTree.cpp "Code").
<!--more-->

#My Solution
I solve this problem in C++, as below:

	/**
	 * Definition for binary tree
	 * struct TreeNode {
	 *     int val;
	 *     TreeNode *left;
	 *     TreeNode *right;
	 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
	 * };
	 */
	 #include<iostream>
	 #include<math>
	 using namespace std;
	 
	class Solution {
	public:
	    bool isBalanced(TreeNode *root) {
	    	int theDepth;
			return isTreeBalanced(root, &theDepth); 
	    }
	    bool isTreeBalanced(TreeNode *theRoot, int *theDepth) 
	    {
	    	if(theRoot == NULL)
	    	{
	    		*theDepth = 0;
	    		return true;
	    	}
	    	int leftDepth, rightDepth;
	    	if(isTreeBalanced(theRoot->left, &leftDepth) && isTreeBalanced(theRoot->right, &rightDepth))
	    	{
	    		int diffDepth = abs(leftDepth - rightDepth);
	    		if(diffDepth <= 1)
	    		{
	    			*theDepth = 1 + (leftDepth > rightDepth ? leftDepth : rightDepth);
	    			return true;
	    		}
	    	}
	    	return false;
	    }
	};


#Note
To reduce the time complexity, I put the depth as the function parameter and recursively judge whether the left and right of the tree is the balanced tree and the difference of depth of two subtrees is less or equal to 1.