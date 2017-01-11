title: LeetCode Convert Sorted List to Binary Search Tree
date: 2015-07-14 08:51:06
tags: leetcode
---


# Description
Given a singly linked list where elements are sorted in ascending order, convert it to a height balanced BST.

The original problem is [here](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ConvertSortedListToBinarySearchTree.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Convert Sorted List to Binary Search Tree
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stack>
	#include<stdlib.h>
	using namespace std;
	
	/**
	 * Definition for singly-linked list.
	 * struct ListNode {
	 *     int val;
	 *     ListNode *next;
	 *     ListNode(int x) : val(x), next(NULL) {}
	 * };
	 */
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
	    TreeNode* sortedListToBST(ListNode* head) {
	    	if(head == NULL)
	    		return NULL;
	        TreeNode *root = new TreeNode(-1);
	        if(head->next == NULL){
	        	root->val = head->val;
	        	return root;
	        }
	        	
	        ListNode *before, *slow, *fast;
	        before=head;
			slow = head;
	        fast = head;
	        while(fast->next!=NULL && fast->next->next!=NULL){
	        	if(slow != head)
	        		before = before->next;
				slow = slow->next;
	        	fast = fast->next->next;
	        }
	        if(fast->next == NULL){
	        	fast = slow;
	        	before->next = NULL;
	        }
	        else{
		       	fast = slow->next;
	        	slow->next = NULL;
	        }
	
	        root->val = fast->val;
	        root->left  = sortedListToBST(head);
	        if(fast->next != NULL)
	        	root->right = sortedListToBST(fast->next);
	        else
	        	root->right = NULL;
	        
			return root;
	    }
	};

# Note
Because the array is sorted, so the middle of the list is the root of the tree(I use two pointer slow and fast to find the middle node of the list). Then the the left and right parts of the root contains the elements before and after the middle, respectively . Recursively, the binary search tree can be built. 
