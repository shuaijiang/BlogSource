title: LeetCode Linked List Cycle
date: 2015-07-09 16:10:52
tags: leetcode
---

# Description


The original problem is [here](https://leetcode.com/problems/linked-list-cycle/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/LinkedListCycle.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*Linked List Cycle
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
	    bool hasCycle(ListNode *head) {
	        map<ListNode*,int> myMap;
			if(head == NULL) 
				return false;
			if(head->next == NULL)
				return false;
			ListNode * node = head;
			while(node!=NULL){
				if(myMap.find(node)==myMap.end())
					myMap[node] = 1;
				else
					return true;
				node = node->next;
			}
			return false;
	    }
	};

# Note
To solve the problem, a hash(map in C++) is need to judge whether a node is unique in the list. 
