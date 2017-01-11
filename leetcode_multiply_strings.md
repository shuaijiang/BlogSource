title: LeetCode Multiply Strings
date: 2015-08-01 10:58:26
tags: leetcode
---

# Description
Given two numbers represented as strings, return multiplication of the numbers as a string.

Note: The numbers can be arbitrarily large and are non-negative.

The original problem is [here](https://leetcode.com/problems/multiply-strings/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/MultiplyStrings.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Multiply Strings 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<math.h>
	#include<vector>
	#include<string>
	#include<stdlib.h>
	using namespace std;
	 
	class Solution {
	public:
	    string multiply(string num1, string num2) {
	  		int size1 = num1.size();
	  		int size2 = num2.size();
	  		vector<int> result(size1+size2,0);
	  		int k = size1+size2-2;
	  		for(int i=0;i<size1;i++){
	  			int n1 = num1[i]-'0';
	  			for(int j=0;j<size2;j++){
	  				int n2 = num2[j]-'0';
	  				result[k-i-j] += n1 * n2;
	  			}
	  		}
	  		int carries = 0;
			for(int i=0;i<size1+size2;i++){
				result[i] += carries;
				if(result[i] > 9){
					carries = result[i]/10;
					result[i] = result[i] % 10;
				}
				else
					carries = 0;
			}
			int i = size1+size2-1;
			while(result[i] == 0)
				i--;
			string str;
			for(int j=i;j>=0;j--){
				str.push_back(result[j]+'0');
			}
			if(str == "")
				str.push_back('0');
			return str;
	    }
	};

# Note
To simplify the problem, reference to [blog](http://www.cnblogs.com/TenosDoIt/p/3735309.html). 
