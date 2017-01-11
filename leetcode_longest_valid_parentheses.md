title: LeetCode Longest Valid Parentheses
date: 2015-09-09 15:37:45
tags: leetcode
---

# Description
Given a string containing just the characters '(' and ')', find the length of the longest valid (well-formed) parentheses substring.

For "(()", the longest valid parentheses substring is "()", which has length = 2.

Another example is ")()())", where the longest valid parentheses substring is "()()", which has length = 4.

The original problem is [here](https://leetcode.com/problems/longest-valid-parentheses/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/LongestValidParentheses.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Longest Valid Parentheses 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stack>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int longestValidParentheses(string s) {
	        int len = s.size();
	        if( len <= 0)
	        	return 0;
	        stack<int> myStack; // save the index of '('
	        int maxLen = 0, last = -1;
	        for(int i=0; i<len; i++){
	        	if(s[i] == '(')
					myStack.push(i);
				else{
					if(!myStack.empty()){
						myStack.pop();
						if(myStack.empty())
							maxLen = max(maxLen, i-last);
						else
							maxLen = max(maxLen, i-myStack.top());
					}
					else{
						last = i;
					}
				}
	        }
	        return maxLen;
	    }
	};

# Note
To solve the problem, a stack is used to save the index of '('. If the current char is ')', pop the stack if it is not empty; otherwise, let last = the current index. After pop the stack, if the stack is empty, then get the length of new group valid parentheses by i-last; else, the length is i-stack.top(). 
