title: LeetCode Reorder List
date: 2015-06-30 23:05:28
tags: leetcode
---


# Description
Given a singly linked list L: L0→L1→…→Ln-1→Ln,
reorder it to: L0→Ln→L1→Ln-1→L2→Ln-2→…

You must do this in-place without altering the nodes' values.

For example,
Given {1,2,3,4}, reorder it to {1,4,2,3}.

The original problem is [here](https://leetcode.com/problems/reorder-list/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ReorderList.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*
	*Reorder List 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stack>
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
	    void reorderList(ListNode* head) {
	        if(head==NULL)
	        	return;
	        if(head->next==NULL)
	        	return;
	        ListNode* node;
	        vector<ListNode*> vec;
	        int totalNum = 0;
	        node = head->next;
	        while(node!=NULL){
	        	vec.push_back(node);
	        	node = node->next;
	        }
	        int size = vec.size();
	        node = head;
	        for(int i=0;i<size/2;i++){
	        	node->next = vec[size-1-i];
	        	node = node->next;
	        	node->next = vec[i];
	        	node = node->next;
	        }
	        if(size%2!=0){
	        	node->next = vec[size/2];
	        	node = node->next;
	        }
	        node->next=NULL;
	    }
	};

# Note
To solve the problem, use a vector to save the list and reconstruct the list. 
