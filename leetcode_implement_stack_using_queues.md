title: LeetCode Implement Stack Using Queues
date: 2015-07-10 23:32:48
tags: leetcode
---


# Description
Implement the following operations of a stack using queues.

- push(x) -- Push element x onto stack.
- pop() -- Removes the element on top of the stack.
- top() -- Get the top element.
- empty() -- Return whether the stack is empty.

The original problem is [here](https://leetcode.com/problems/implement-stack-using-queues/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ImplementStackUsingQueues.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*Implement Stack using Queues 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<queue>
	#include<stdlib.h>
	
	class Stack {
	public:
		queue<int> myQueue;
	    // Push element x onto stack.
	    void push(int x) {
	        myQueue.push(x);
	    }
	
	    // Removes the element on top of the stack.
	    void pop() {
	        queue<int> queue2;
	        int num;
	        while(myQueue.size() > 1){
	        	num = myQueue.front();
	        	myQueue.pop();
	        	queue2.push(num);
	        }
	        myQueue = queue2;
	    }
	
	    // Get the top element.
	    int top() {
	        return myQueue.back();
	    }
	
	    // Return whether the stack is empty.
	    bool empty() {
	        return myQueue.empty();
	    }
	};

# Note
For the pop, we need pop all the data to a new queue except the final number. 
