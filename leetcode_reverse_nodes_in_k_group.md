title: LeetCode Reverse Nodes In K Group
date: 2015-07-23 15:46:48
tags: leetcode
---

# Description
Given a linked list, reverse the nodes of a linked list k at a time and return its modified list.

If the number of nodes is not a multiple of k then left-out nodes in the end should remain as it is.

You may not alter the values in the nodes, only nodes itself may be changed.

Only constant memory is allowed.

For example,
Given this linked list: 1->2->3->4->5

For k = 2, you should return: 2->1->4->3->5

For k = 3, you should return: 3->2->1->4->5

The original problem is [here](https://leetcode.com/problems/reverse-nodes-in-k-group/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ReverseNodesInKGroup.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Reverse Nodes in k-Group 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
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
	class Solution {
	public:
	    ListNode* reverseKGroup(ListNode* head, int k) {
	    	if(head == NULL || head->next == NULL)
	    		return head;
	    	if(k <= 1)
	    		return head;
	    	
	        stack<ListNode*> myStack;
	        ListNode* node=NULL, *lastNode=NULL;
	
	        node = head;
	        int i = 0;
	        while(node != NULL){
	        	myStack.push(node);
	        	node = node->next;
	        	i ++;
	        	if(i%k == 0){
	        		if(i==k){
	        			if(!myStack.empty())
	        				head = myStack.top();
	        			lastNode = head;
	        			myStack.pop();
	        		}
	        		while(!myStack.empty()){
	        			lastNode->next = myStack.top();
	        			myStack.pop();
	        			lastNode = lastNode->next;
	        			lastNode->next = NULL;
	        		}
	        	}
	        }
	        if(lastNode == NULL)
	        	return head;
	        
	        while(!myStack.empty()){
	        	node = myStack.top();
	        	myStack.pop();
	        }
	        if(node!=NULL)
	        	lastNode->next = node;
	        
			return head;
	    }
	};


# Note
To solve the problem, stack is used to save each group of nodes and reverse the nodes. Finally, joint groups together to a new linked list.
