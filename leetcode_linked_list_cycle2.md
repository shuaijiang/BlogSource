title: LeetCode Linked List Cycle2
date: 2015-07-09 18:55:48
tags: leetcode
---

# Description


The original problem is [here](https://leetcode.com/problems/linked-list-cycle-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/LinkedListCycle2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*Linked List Cycle2
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<map>
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
	    ListNode *detectCycle(ListNode *head) {
	        map<ListNode*,int> myMap;
			if(head == NULL) 
				return NULL;
			if(head->next == NULL)
				return NULL;
			ListNode * node = head;
			while(node!=NULL){
				if(myMap.find(node)==myMap.end())
					myMap[node] = 1;
				else
					return node;
				node = node->next;
			}
			return NULL;
	    }
	};

# Note
To solve the problem, a hash(map in C++) is need to judge whether a node is unique in the list. 
