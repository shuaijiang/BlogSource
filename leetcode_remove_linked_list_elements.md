title: LeetCode Remove Linked List Elements
date: 2015-07-09 10:38:39
tags: leetcode
---

# Description

Given two binary trees, write a function to check if they are equal or not.

Two binary trees are considered equal if they are structurally identical and the nodes have the same value.

The original problem is [here](https://leetcode.com/problems/remove-linked-list-elements/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/RemoveLinkedListElements.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*Remove Linked List Elements 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
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
	class Solution {
	public:
	    ListNode* removeElements(ListNode* head, int val) {
			while(head != NULL && head->val == val)
				head = head->next;
			
			if(head == NULL)
	        	return NULL;
			ListNode *lastNode = head;
			ListNode *currNode = head->next;
			while(currNode != NULL) {
				if(currNode->val == val){
					lastNode->next = currNode->next;
					currNode = currNode->next;
				}
				else{
					lastNode = lastNode->next;
					currNode = currNode->next;
				}
			}
			return head;		
	    }
	};


# Note
To solve the problem, we traversal the list and remove the node whos value is equal to val. 
