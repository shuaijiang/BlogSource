title: LeetCode Simplify Path
date: 2015-08-26 21:10:20
tags: leetcode
---


# Description
Given an absolute path for a file (Unix-style), simplify it.

For example,
path = "/home/", => "/home"
path = "/a/./b/../../c/", => "/c"


The original problem is [here](https://leetcode.com/problems/simplify-path/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/SimplifyPath.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Simplify Path
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stack>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    string simplifyPath(string path) {
	        string result;
	        int size = path.size();
	        stack<string> myStack;
			string onePart;
			int i=0,j=0;
			for(;i<size;i++){
				int len = i-j-1;
				if(path[i] == '/'){
					if(len > 0){
						onePart = path.substr(j+1,len);
						if(onePart == ".")
							;
						else if(onePart == ".."){
							if(!myStack.empty())
								myStack.pop();
						}
						else
							myStack.push(onePart);
					}				
					j = i;
				}
				else if(i == size - 1 && len >= 0){
					onePart = path.substr(j+1,len+1);
					if(onePart == ".")
						;
					else if(onePart == ".."){
						if(!myStack.empty())
							myStack.pop();
					}
					else
						myStack.push(onePart);
				}
			}
	
			while(!myStack.empty()){
				if(result.size() == 0)
					result = myStack.top();
				else
					result = myStack.top() + "/" + result;
				myStack.pop();
			}
			result = "/" + result;
			return result;
	    }
	};

# Note
To solve the problem, a stack is used to save every part of the path. If reach ".", ignore it, if reach "..", pop the stack.  
