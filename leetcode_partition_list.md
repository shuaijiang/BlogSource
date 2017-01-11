title: LeetCode Partition List
date: 2015-07-21 16:12:20
tags: leetcode
---

# Description
Given a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x.

You should preserve the original relative order of the nodes in each of the two partitions.

For example,
Given 1->4->3->2->5->2 and x = 3,
return 1->2->2->4->3->5.

The original problem is [here](https://leetcode.com/problems/partition-list/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/PartitionList.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Partition List 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<queue>
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
	    ListNode* partition(ListNode* head, int x) {
	    	if(head == NULL)
	    		return head;
	        queue<ListNode*> largeQueue, smallQueue;
	        ListNode * node = head;
	        while(node != NULL){
	        	if(node->val >= x)
	        		largeQueue.push(node);
	        	else
	        		smallQueue.push(node);
				node = node->next;
	        }
	        head = NULL;
	        if(!smallQueue.empty()){
	        	head = smallQueue.front();
	        	smallQueue.pop(); 
	        	node = head;
	        	while(!smallQueue.empty()){
		        	node->next = smallQueue.front();
		        	node = node->next;
		        	smallQueue.pop();
		        }
	        }
			if(head == NULL){
				head = largeQueue.front();
				largeQueue.pop();
				node = head;
			}
			while(!largeQueue.empty()){
				node->next = largeQueue.front();
				largeQueue.pop();
				node = node->next;
			}
			node->next = NULL;
			return head;
	    }
	};

# Note
To solve the problem, two queues are used. During traversal the list, put the node which is smaller than x to one queue, put the node which is larger or equal to x to the other queue. And to build the new list, the small node queue is at front, the large queue is at back.
