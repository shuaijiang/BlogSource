title: LeetCode Basic Calculator
date: 2015-06-28 16:13:25
tags: leetcode
---


# Description
Implement a basic calculator to evaluate a simple expression string.

The expression string may contain open ( and closing parentheses ), the plus + or minus sign -, non-negative integers and empty spaces .

You may assume that the given expression is always valid.

Some examples:

	"1 + 1" = 2
	" 2-1 + 2 " = 3
	"(1+(4+5+2)-3)+(6+8)" = 23

The original problem is [here](https://leetcode.com/problems/basic-calculator/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/BasicCalculator.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Basic Calculator
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stack>
	#include<string.h>
	#include<sstream>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int calculate(string s) {
	    	stack<char> myStack;
	    	string substr="",totalStr;
	        int sign=1;
	        int num=0, total = 0;
	        for(int i=0;i<s.length();i++){
	        	if(s[i]=='(' || s[i]=='+' || s[i]=='-')
	        		myStack.push(s[i]);
	        	else if(s[i]>='0' && s[i]<='9'){
	        		myStack.push(s[i]);
	        	}
	        	else if(s[i]==')'){
					while(myStack.top() != '('){
						substr.push_back(myStack.top());
						myStack.pop();
					}
					myStack.pop();
					totalStr = compute(substr);
					//cout<<"totalStr="<<totalStr<<endl;
					
					if(totalStr[0]=='-' && !myStack.empty()){
						if(myStack.top()=='+')
							myStack.pop();
						if(myStack.top()=='-'){
							totalStr[0] = '+';
							myStack.pop();
						}
					}
					for(int j=0;j<totalStr.length();j++){
						myStack.push(totalStr[j]) ;
					}
					substr="";
	        	}
	        }
	        while(!myStack.empty()){
	        	substr.push_back(myStack.top());
	        	myStack.pop();
	        }
	        totalStr = compute(substr);
	        substr="";
			total = atoi(totalStr.c_str()) ;
	        return total;
	    }
	    string compute(string str){
	    	string s,totalStr;
	    	stringstream ss;
	    	for(int i=str.length()-1;i>=0;i--){
	    		s.push_back(str[i]);
	    	}
	    	int sign=1;
	        int num=0, total = 0;
	        for(int i=0;i<s.length();i++){
	        	if(s[i]>='0' && s[i]<='9'){
	        		num = num * 10 + (s[i]-'0');
	        	}
	        	else{
	        		total = total + sign * num;
	        		num = 0;
	        		if(s[i]== '+')
	        			sign = 1;	
	        		else if(s[i]=='-')
						sign = -1;
	        	}
	        }
	        total += sign * num;
	        ss<<total;
	        ss>>totalStr;
	        return totalStr;
	    }
	};
	//The code under below is used for test
	int main(){
		string str("(5-(1+(5)))");
		Solution s;
		int result = s.calculate(str);
		cout<<"result="<<result<<endl;
		system("pause");
		return 0;
	}

# Note
To solve the problem, a stack is need to deal with the "(" and ")". 
