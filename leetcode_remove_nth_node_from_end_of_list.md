title: LeetCode Remove Nth Node From End Of List
date: 2015-06-20 15:20:01
tags: leetcode
---


# Description
Given a linked list, remove the nth node from the end of list and return its head.

For example,

   Given linked list: 1->2->3->4->5, and n = 2.

   After removing the second node from the end, the linked list becomes 1->2->3->5.

Note:
Given n will always be valid.
Try to do this in one pass.

The original problem is [here](https://leetcode.com/problems/remove-nth-node-from-end-of-list/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/RemoveNthNodeFromEndOfList.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	
	/*
	*Remove Nth Node from End of List 
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
	    ListNode* removeNthFromEnd(ListNode* head, int n) {
	    	if(head==NULL)
	    		return NULL;
	    	if(head->next == NULL && n == 1)
	    		return NULL;
	        ListNode *ptr, *ptr_nth, *ptr_before;
	        int count  = 0;
	        ptr = head;
	        ptr_nth    = head;
			ptr_before = head;
			while(ptr->next != NULL){
				if(count > n){
	        		ptr_before = ptr_nth;
					ptr_nth = ptr_nth->next;
	        	}
	        	count ++;
	        	ptr = ptr->next;
			}
			if(ptr_before == ptr_nth)
				head = head->next;
			else
	        	ptr_before->next = ptr_nth->next;
	        	
	        return head;
	    }
	};



# Note
To solve the problem, we need three pointers, one pointer traverse the list and the second one point the element which always keeps n distance to the first pointer. The third pointer will always before the second one. Finally, after traverse the list, remove the element which pointed by the second pointer.
