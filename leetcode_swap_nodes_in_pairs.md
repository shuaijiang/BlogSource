title: LeetCode: Swap Nodes in Pairs
date: 2015-04-04 23:31:29
tags: leetcode
---

#Description
Given a linked list, swap every two adjacent nodes and return its head.

For example,
Given 1->2->3->4, you should return the list as 2->1->4->3.

Your algorithm should use only constant space. You may not modify the values in the list, only nodes itself can be changed.

The original problem is [here](https://leetcode.com/problems/swap-nodes-in-pairs/ "Problem").

My code is [here](https://github.com/shuaijiang/LeetCode/blob/master/SwapNodesInPairs.cpp "Code").

<!--more-->

#My Solution
I solve this problem in C++, as below:

	/*
	*Swap Nodes in Pairs
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	
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
	    ListNode *swapPairs(ListNode *head) {
	    	if(head == NULL)
	    		return head;
			if(head->next == NULL)
				return head;
			
	        ListNode * currentNode = head->next;
	        ListNode * lastNode = head;
	        ListNode * tempNode;
			if(head->next != NULL)
	        {
	        	tempNode = head;
	        	head = head->next;
	        	tempNode->next = head->next; 
	        	head->next = tempNode;
	        	lastNode = head->next;
	        	currentNode = lastNode->next;
	        }
	        while(currentNode != NULL )
	        {
	        	if(currentNode->next == NULL)
	        		break;
				tempNode = currentNode;
				currentNode = currentNode->next;
				tempNode->next = currentNode->next;
				currentNode->next = tempNode;
				
				lastNode->next = currentNode;
				
				lastNode    = currentNode->next;
				currentNode = lastNode->next;
	        }
	        return head;
	    }
	};


#Note

1. We must swap the nodes instead of values.
2. When swap two nodes, we must assign the next value of the last node to  the current node.