title: LeetCode String To Integer
date: 2015-07-26 12:16:15
tags: leetcode
---

# Description
Implement atoi to convert a string to an integer.

The original problem is [here](https://leetcode.com/problems/string-to-integer-atoi/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/StringToInteger.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*String To Integer
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<string.h>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int myAtoi(string str) {
	        double result = 0.0;
	        int flag = 1, work = 0;
			int size = str.size(), i = 0;
			while(str[i] == ' ')
				i++;
			if(str[i] == '-'){
				i ++;
				flag = 0;
			}
			else if(str[i] == '+')
			{
				i++;
				flag = 1;
			}
			
			for(;i<size;i++){
				if(str[i]>='0' && str[i]<='9'){
					result = result * 10 + (str[i] - '0');
					work = 1;
				}
				else
					break;
			}
			if(work == 0)
				return 0;
			if(flag == 1 && result  >= INT_MAX)
				return INT_MAX;
			if(flag == 0 && result > INT_MAX)
				return INT_MIN;
			
			int myInt = (int) result;
			if(flag == 0)
				myInt = -1 * myInt;
			return myInt;
	    }
	};

# Note
To solve the problem, first discards as many whitespace characters as necessary until the first non-whitespace character is found.

When occur additional characters after those that form the integral number, stop the function, and return the current result. 

If no valid conversion could be performed, a zero value is returned. If the correct value is out of the range of representable values, INT_MAX (2147483647) or INT_MIN (-2147483648) is returned.
