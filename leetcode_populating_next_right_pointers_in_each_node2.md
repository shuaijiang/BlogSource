title: LeetCode Populating Next Right Pointers in Each Node 2
date: 2015-07-10 10:58:39
tags: leetcode
---

# Description
Follow up for problem "Populating Next Right Pointers in Each Node".

What if the given tree could be any binary tree? Would your previous solution still work?

Note:

You may only use constant extra space.
For example,
Given the following binary tree,

	         1
	       /  \
	      2    3
	     / \    \
	    4   5    7

After calling your function, the tree should look like:

         1 -> NULL
       /  \
      2 -> 3 -> NULL
     / \    \
    4-> 5 -> 7 -> NULL

The original problem is [here](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/PopulatingNextRightPointersInEachNode2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Populating Next Right Pointers in Each Node 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	/**
	 * Definition for binary tree with next pointer.
	 * struct TreeLinkNode {
	 *  int val;
	 *  TreeLinkNode *left, *right, *next;
	 *  TreeLinkNode(int x) : val(x), left(NULL), right(NULL), next(NULL) {}
	 * };
	 */
	class Solution {
	public:
	    void connect(TreeLinkNode *root) {
	    	if(root == NULL)
	    		return;
	        vector<TreeLinkNode*> currLevel;
	        vector<TreeLinkNode*> nextLevel;
	        currLevel.push_back(root);
	        while(currLevel.size()>0){
	        	for(int i=0;i<currLevel.size();i++){
		        	TreeLinkNode * node = currLevel[i];
		        	if(i+1<currLevel.size())
		        		node->next = currLevel[i+1];
		        	if(node->left != NULL)
						nextLevel.push_back(node->left);
		        	if(node->right != NULL)
		        		nextLevel.push_back(node->right);
		        }
		        currLevel = nextLevel;
		        nextLevel.clear();
	        }
	    }
	};

# Note
To solve the problem, I use a vector to save the nodes of each level, and Populat next pointer of each node to point to its next right node.
