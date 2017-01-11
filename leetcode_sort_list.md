title: LeetCode Sort List
date: 2015-07-13 23:01:33
tags: leetcode
---

# Description
Sort a linked list in O(n log n) time using constant space complexity.

The original problem is [here](https://leetcode.com/problems/sort-list/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/SortList.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Sort List
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
	class Solution {
	public:
	    ListNode* sortList(ListNode* head) {
	        if(head==NULL)
	        	return head;
	        if(head->next==NULL)
	        	return head;
			ListNode *slow, *fast;
	        slow = head, fast = head;
	        while(fast->next != NULL && fast->next->next != NULL){
	        	slow = slow->next;
	        	fast = fast->next->next;
	        }
	        fast = slow->next;
	        slow->next = NULL;
	        
	        ListNode *l1 = sortList(head);
	        ListNode *l2 = sortList(fast);
	        ListNode *l3 = mergeTwoLists(l1,l2);
	        return l3;
	    }
	    ListNode* mergeTwoLists(ListNode *l1, ListNode *l2){
	    	ListNode node(-1);
	    	for(ListNode *p = &node;l1!=NULL || l2!=NULL;p=p->next){
	    		int val1 = l1 == NULL ? INT_MAX : l1->val;
	    		int val2 = l2 == NULL ? INT_MAX : l2->val;
	    		if(val1<=val2){
	    			p->next = l1;
	    			l1 = l1->next;
	    		}
	    		else{
	    			p->next = l2;
	    			l2 = l2->next;
	    		}
	    	}
	    	return node.next;
	    }
	};

# Note
To solve the problem, use a low pointer and a fast pointer to divide the list to two sorted list from the middle. And then merge the two sorted lists into one sorted list. The sort list is a recursive function, until divide the list into only one node. 
