title: LeetCode Reverse Linked List 2
date: 2015-07-20 19:11:28
tags: leetcode
---


# Description
Reverse a linked list from position m to n. Do it in-place and in one-pass.

For example:
Given 1->2->3->4->5->NULL, m = 2 and n = 4,

return 1->4->3->2->5->NULL.

Note:
Given m, n satisfy the following condition:
1 ≤ m ≤ n ≤ length of list.

The original problem is [here](https://leetcode.com/problems/reverse-linked-list-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ReverseLinkedList2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Reverse Linked List II
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
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
	    ListNode* reverseBetween(ListNode* head, int m, int n) {
	        if(head == NULL || head->next == NULL)
	        	return head;
	        if(m>n)
	        	return NULL;
	        if(m==n)
	        	return head;
	        
	        ListNode * newHead;
	        ListNode * lastNode, *currNode, *nextNode, *node;
	        if(n<=1)
	        	return head;
	        
	        node = head;
			for(int i=1;i<n;i++){
				node = node->next;
			}
			nextNode = node->next;
			
			if(m==1){
				newHead = reverseList(head, n-m+1);
				head->next = nextNode;
				return newHead; 
			}
			else{
				lastNode = head;
				currNode = head->next;
				for(int i=2;i<m;i++){
					lastNode = lastNode->next;
					currNode = currNode->next; 
				}
				newHead = reverseList(currNode,n-m+1);
				currNode->next = nextNode;
				lastNode->next = newHead;
			}
			return head;
	    }
	    ListNode* reverseList(ListNode* head, int k){
	    	stack<ListNode*> myStack;
	    	ListNode* newHead, *node, *nextNode;
	    	node = head;
	    	myStack.push(node);
	    	for(int i=1;i<k;i++){
	    		node = node->next;
	    		myStack.push(node);
	    	}
	    	newHead = node;
	    	myStack.pop();
	    	while(!myStack.empty()){
	    		nextNode = myStack.top();
	    		myStack.pop();
	    		node->next = nextNode;
	    		node = node->next;
	    	}
	    	return newHead;
	    }
	};



# Note
To solve the problem, first, we need to get the head and tail of list need to reverse. Then, reverse the list(from m to n). Finally, join the new list to the original one.
