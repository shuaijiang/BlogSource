title: LeetCode Rotate List
date: 2015-07-02 19:36:04
tags: leetcode
---


# Description
Given a list, rotate the list to the right by k places, where k is non-negative.

For example:
Given 1->2->3->4->5->NULL and k = 2,
return 4->5->1->2->3->NULL.

The original problem is [here](https://leetcode.com/problems/rotate-list/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/RotateList.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Rotate List  
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
	    ListNode* rotateRight(ListNode* head, int k) {
	    	if(head == NULL)
	    		return head;
	        int nodeSize = 0;
	        vector<ListNode*> vec;
	        ListNode* node = head;
	        
	        while(node!=NULL){
	        	vec.push_back(node);
	        	node=node->next;
	        }
	        nodeSize = vec.size();
	        k = k % nodeSize;
	        if(k==0)
	        	return head;
	        
	        head = NULL;
	        
	        for(int i=0;i<k;++i){	
	        	node = vec[nodeSize-1-i];
	        	if(i==0)
	        		node->next = vec[0];
	        	else
					node->next = head;
				head = node;
	        }
	        node = vec[nodeSize-1-k];
			node->next = NULL;
	        return head;
	    }
	};

# Note
If k is larger than the number of nodes, we need to modular k by the number of nodes. 
