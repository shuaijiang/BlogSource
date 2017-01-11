title: LeetCode Intersection of Two Linked Lists
date: 2015-06-22 21:13:33
tags: leetcode
---


# Description

The original problem is [here](https://leetcode.com/problems/intersection-of-two-linked-lists/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/IntersectionOfTwoLinkedLists.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*
	*Intersection of Two Linked Lists 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<math.h>
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
	    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
	        ListNode *listA=headA, *listB=headB;
			if(listA==NULL || listB==NULL)
	        	return NULL;
			
			int lenA=0,lenB=0;
	        lenA = lengthOfList(listA);
	        lenB = lengthOfList(listB);
	        
	        while(lenA > lenB){
	        	listA = listA->next;
	        	lenA --;
	        }
	        while(lenB > lenA){
	        	listB = listB->next;
	        	lenB --;
	        }
	        while(listA!=NULL && listB != NULL){
	        	if(listA == listB)
	        		return listA;
	        	listA = listA->next;
				listB = listB->next;
	        }
	        return NULL;
	    }
	    int lengthOfList(ListNode * head){
	    	ListNode *list=head;
	    	int len = 0;
	    	while(list != NULL)
	    	{
	    		len ++ ;
	    		list = list->next;
	    	}
	    	return len;
	    }
	};


# Note
The two linked lists have the same list in the end. So, I get the longer list of the two and skip the redundants at the begining. Then, the two lists have same length, we can traverse them and find the first same node. 
