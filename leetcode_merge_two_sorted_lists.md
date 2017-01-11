title: LeetCode Merge Two Sorted Lists
date: 2015-06-25 10:12:26
tags: leetcode
---


# Description
Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

The original problem is [here](https://leetcode.com/problems/merge-two-sorted-lists/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/MergeTwoSortedLists.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Merge Two Sorted Lists
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<math.h>
	#include<vector>
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
	    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
	    	if(l1 == NULL && l2 != NULL)
	    		return l2;
	    	if(l1 != NULL && l2 == NULL)
	    		return l1;
	    	if(l1 == NULL && l2 == NULL)
	    		return NULL;
	        
			ListNode *head, *list;
	        if(l1->val < l2->val){
	        	head = l1;
				l1 = l1->next;	
	        }
	        else{
	        	head = l2;
	        	l2 = l2->next;
	        }
			list = head;
			while(l1!=NULL && l2!=NULL){
				if(l1->val < l2->val){
					list->next = l1;
					list = list->next;
					l1 = l1->next;
				}
				else{
					list->next = l2;
					list = list->next;
					l2 = l2->next;
				}
			}
			if(l1 != NULL)
				list->next = l1;
			if(l2 != NULL)
				list->next = l2;
			
			return head;
			
	    }
	};


# Note
To solve the problem, merge sort algorithm is need.  
