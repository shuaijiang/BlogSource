title: LeetCode Sum Root to Leaf Numbers
date: 2015-06-26 11:25:06
tags: leetcode
---

# Description

Given a binary tree containing digits from 0-9 only, each root-to-leaf path could represent a number.

An example is the root-to-leaf path 1->2->3 which represents the number 123.

Find the total sum of all root-to-leaf numbers.

For example,

   1
   / \
  2   3

The root-to-leaf path 1->2 represents the number 12.
The root-to-leaf path 1->3 represents the number 13.
Return the sum = 12 + 13 = 25.

The original problem is [here](https://leetcode.com/problems/sum-root-to-leaf-numbers/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/SumRootToLeafNumbers.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*
	*Maximum Depth of Binary Tree
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<math.h>
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
	struct TreeNode {
	 	int val;
	    TreeNode *left;
	    TreeNode *right;
	    TreeNode(int x) : val(x), left(NULL), right(NULL) {}
	 };
	class Solution {
	public:
		int sum;
	    int sumNumbers(TreeNode* root) {
	    	if(root == NULL)
	    		return 0;
	        if(root->left == NULL && root->right == NULL)
	        	return root->val;
	        sum = 0;
			sumNum(root,0);
			return sum;
	    }
	    void sumNum(TreeNode * root, int num){
	    	if(root == NULL)
	    		return;
	    	num = twoSum(num,root->val);
	    	if(root->left == NULL && root->right == NULL)
	    		sum += num;    	
	
	    	if(root->left != NULL)
	    		sumNum(root->left,num);
	    	if(root->right != NULL)
	    		sumNum(root->right,num);
	    }
	    int twoSum(int a, int b) {
	    	int bNum = b, aNum = a;
	    	if(bNum == 0)
	    		aNum = aNum * 10;
	    	while(bNum>0){
	    		aNum = aNum * 10;
	    		aNum = aNum + bNum;
	    		bNum = bNum / 10;
	    	}
	    	return aNum;
	    }
	};



# Note
In the solution, recursion is needed. Function twoSum is used for combine two numbers to a new one. When we visit to a leaf node, we can get the sum of one path. Finally, we can add all the sums, and get the result.
