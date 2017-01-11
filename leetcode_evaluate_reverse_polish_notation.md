title: LeetCode Evaluate Reverse Polish Notation
date: 2015-07-24 15:38:53
tags: leetcode
---

# Description
Evaluate the value of an arithmetic expression in Reverse Polish Notation.

Valid operators are +, -, *, /. Each operand may be an integer or another expression.

Some examples:

	["2", "1", "+", "3", "*"] -> ((2 + 1) * 3) -> 9
	["4", "13", "5", "/", "+"] -> (4 + (13 / 5)) -> 6

The original problem is [here](https://leetcode.com/problems/evaluate-reverse-polish-notation/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/EvaluateReversePolishNotation.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Evaluate Reverse Polish Notation
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector> 
	#include<stack>
	#include<sstream>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int evalRPN(vector<string>& tokens) {
	        int size = tokens.size();
	        stack<string> myStack;
	        stringstream ss;
	        for(int i=0;i<size;i++){
	        	if(tokens[i]=="+" || tokens[i]=="-" || tokens[i]=="*" || tokens[i]=="/"){
	        		int num2;
					ss<<myStack.top();
	        		ss>>num2;
	        		ss.clear();
	        		myStack.pop();
	        		int num1;
					ss<<myStack.top();
	        		ss>>num1;
	        		ss.clear();
	        		myStack.pop();
	        		int num = 0;
	        		if(tokens[i]=="+")
	        			num = num1 + num2;
	        		else if(tokens[i]=="-")
	        			num = num1 - num2;
	        		else if(tokens[i]=="*")
	        			num = num1 * num2;
	        		else
	        			num = num1 / num2;
	        		string strNum;
	        		ss<<num;
	        		ss>>strNum;
	        		ss.clear();
	        		myStack.push(strNum);
	        	}
	        	else
	        		myStack.push(tokens[i]);
	        }
			int result;
	        ss<<myStack.top();
	        ss>>result;
	        ss.clear();
	        return result;
	    }
	};



# Note
To solve the problem, we need a stack to save the string. If one string is operator, we compute the expression with the two nums in the top of the stack.
Finally, we can get one number, which is the final result.
