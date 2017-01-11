title: LeetCode Reverse Linked List
date: 2015-06-23 11:25:00
tags: leetcode
---


# Description
Reverse a singly linked list.

The original problem is [here](https://leetcode.com/problems/reverse-linked-list/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ReverseLinkedList.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Reverse Linked List 
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
	    ListNode* reverseList(ListNode* head) {
	    	if(head == NULL) 
	    		return NULL;
	    	ListNode *newList=NULL;
	        ListNode *currentNode=head;
	        while(currentNode != NULL)
	        {
	        	int val = currentNode->val;
	        	currentNode = currentNode->next;
	        	
	        	ListNode *newNode = new ListNode(val);
	        	newNode->val  = val;
	        	newNode->next = newList;
	        	newList = newNode;
	        }
	        return newList;
	    }
	};


# Note
To solve the problem, we traverse the list and create a new list which add elements at the begining of the new list.
