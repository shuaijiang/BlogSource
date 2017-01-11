title: LeetCode Remove Duplicates from Sorted List
date: 2015-06-20 10:33:02
tags: leetcode
---


# Description
Given a sorted linked list, delete all duplicates such that each element appear only once.

For example,
Given 1->1->2, return 1->2.
Given 1->1->2->3->3, return 1->2->3.

The original problem is [here](https://leetcode.com/problems/remove-duplicates-from-sorted-list/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/RemoveDuplicatesFromSortedList.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Remove Duplicates from Sorted List 
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
	    ListNode* deleteDuplicates(ListNode* head) {
	    	if(head == NULL || head->next == NULL)
	    		return head;
	        ListNode *ptr_all = head->next;
	        ListNode *ptr_use = head;
	        while(ptr_all != NULL){
	        	if(ptr_all->val != ptr_use->val){
	        		ptr_use->next = ptr_all;
	        		ptr_use = ptr_use->next;
	        	}
				ptr_all = ptr_all->next;
	        }
	        ptr_use->next = NULL;
	        return head;
	    }
	};


# Note
Firstly, we need judge whether the list is null or only has one elemet or not.
To solve the problem, I use two pointers ptr_all and ptr_use. Then, traverse the list use ptr_all, add the unqiue number to ptr_use.  
