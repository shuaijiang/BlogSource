title: LeetCode Add Binary
date: 2015-07-22 19:02:34
tags: leetcode
---


# Description
Given two binary strings, return their sum (also a binary string).

For example,
a = "11"
b = "1"
Return "100".

The original problem is [here](https://leetcode.com/problems/add-binary/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/AddBinary.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Add Binary
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<string>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    string addBinary(string a, string b) {
	        vector<char> result;
	        string str;
			int sizeA = a.size();
	        int sizeB = b.size();
	        int countA = sizeA-1, countB = sizeB-1; 
	        int Add = 0;
	        
			while(countA>=0 && countB>=0){
				int num = a[countA]-'0' + b[countB]-'0';
				
				if(Add == 1){
					num++;
					Add = 0; 
				}
				
				if(num==2){
					Add = 1;
					num = 0;
				}
				else if(num==3){
					Add = 1;
					num = 1;
				}
				result.push_back(num + '0');
				countA--;
				countB--;
			}
	        while(countA>=0){
	        	int num = a[countA] - '0';
				if(Add == 1){
	        		num++;
	        		Add = 0;
	        	}
	        	if(num == 2){
	        		Add = 1;
	        		num = 0;
	        	}
	        	result.push_back(num + '0');
				countA--;
	        }
	        while(countB>=0){
	        	int num = b[countB] - '0';
				if(Add == 1){
	        		num++;
	        		Add = 0;
	        	}
	        	if(num == 2){
	        		Add = 1;
	        		num = 0;
	        	}
	        	result.push_back(num + '0');
				countB--;
	        }
	        if(Add == 1)
	        	result.push_back('1');
	        for(int i=result.size()-1;i>=0;i--)
	        	str.push_back(result[i]);
	        
	        return str;
	    }
	};

# Note
To solve the problem, just add the two binary from end to begin. Don't forget the carry bit. 
