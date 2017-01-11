title: LeetCode Delete Node In A Linked List
date: 2015-07-16 21:48:19
tags: leetcode
---

# Description
Write a function to delete a node (except the tail) in a singly linked list, given only access to that node.

Supposed the linked list is 1 -> 2 -> 3 -> 4 and you are given the third node with value 3, the linked list should become 1 -> 2 -> 4 after calling your function.

The original problem is [here](https://leetcode.com/problems/delete-node-in-a-linked-list/ "Problem").
The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/DeleteNodeInALinkedList.cpp "Code").

<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Delete Node in a Linked List
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<math.h>
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
	    void deleteNode(ListNode* node) {
	        if(node->next == NULL)
	        	return;
	        ListNode *nextNode = node->next;
	        node->val = nextNode->val;
	        node->next = nextNode->next;
			return;
	    }
	};

# Note
I just copy the value of the next node to the current node, and remove the next node by jump it(set the next of the current node to the next of the next node). 
