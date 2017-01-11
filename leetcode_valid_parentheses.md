title: LeetCode Valid Parentheses
date: 2015-06-24 23:50:17
tags: leetcode 
---


# Description
Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

The brackets must close in the correct order, "()" and "()[]{}" are all valid but "(]" and "([)]" are not.

The original problem is [here](https://leetcode.com/problems/valid-parentheses/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ValidParentheses.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Valid Parentheses 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<math.h>
	#include<stack>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    bool isValid(string s) {
	    	if(s.size() <= 0)
	    		return true;
	    	if(s.size() == 1)
	    		return false;
	        stack<char> myStack;
	        for(int count=0;count<s.size();++count){
	        	if(myStack.empty())
	        		myStack.push(s.at(count));
	        	else{
	        		if(abs(s.at(count) - myStack.top()) <= 2 && abs(s.at(count) - myStack.top()) > 0)
	        			myStack.pop();
	        		else
	        			myStack.push(s.at(count));
	        	}
	        }
	        if(myStack.empty())
				return true;
	        else
	        	return false;
	    }
	};
	
	//The code underblow is used for test
	int main(){
		Solution s;
		string str("[(])");
		bool isV = s.isValid(str);
		cout<<"isValid="<<isV<<endl;
		
		system("pause");
		return 0;
	}


# Note
To solve the problem, stack is need. We traverse the string, if it is match to the top, then pop the stack, otherwise push the char to stack. After we finish the string, if the stack is empty, we can say it is valid, otherwise invalid.
