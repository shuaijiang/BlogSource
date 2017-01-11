title: LeetCode Min Stack
date: 2015-06-24 11:22:13
tags: leetcode
---

# Description
Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

- push(x) -- Push element x onto stack.
- pop() -- Removes the element on top of the stack.
- top() -- Get the top element.
- getMin() -- Retrieve the minimum element in the stack.

The original problem is [here](https://leetcode.com/problems/min-stack/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/MinStack.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Min Stack 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class MinStack {
	public:
		vector<int> stack;
		vector<int> minStack;
		vector<int>::iterator iter, minIter;
		vector<int>::reverse_iterator reiter;
	    void push(int x) {
	        stack.push_back(x);
	        if(minStack.size()<1)
	        	minStack.push_back(x);
	        else{
	        	reiter = minStack.rbegin();
	        	if(x <= *reiter)
	        		minStack.push_back(x);
	        }
	    }
	
	    void pop() {
	    	if(stack.size() < 1)
				return ; 
	        reiter = stack.rbegin();
	        int num = * reiter;
	        reiter = minStack.rbegin();
	        int minNum = *reiter;
	        
	        stack.pop_back();
	        if(num == minNum){
	        	minStack.pop_back();
	        }
	    }
	
	    int top() {
	        reiter = stack.rbegin();
	        return *reiter;
	    }
	
	    int getMin() {
	        reiter = minStack.rbegin();
	        return *reiter;
	    }
	};


# Note
The operations of stack are easy but the getMin, we need create another stack to save the minimum value.
