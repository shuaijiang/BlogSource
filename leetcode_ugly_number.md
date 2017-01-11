title: LeetCode Ugly Number
date: 2015-08-24 21:09:54
tags: leetcode
---

# Description
Write a program to check whether a given number is an ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 6, 8 are ugly while 14 is not ugly since it includes another prime factor 7.

Note that 1 is typically treated as an ugly number.

The original problem is [here](https://leetcode.com/problems/ugly-number/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/UglyNumber.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Ugly Number
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    bool isUgly(int num) {
	    	if(num == 0)
	    		return false;
	    	if(num == 1)
	    		return true;
	        if(num % 2 == 0){
	        	if(num/2 == 0)
	        		return true;
	        	return isUgly(num/2);
	        }
	        	
	        else if(num % 3 == 0){
	        	if(num/3 == 0)
	        		return true;
	        	return isUgly(num/3);
	        }
	        else if(num % 5 == 0){
	        	if(num/5 == 0)
	        		return true;
	        	return isUgly(num/5);
	        }
	        else 
	    		return false;
	    }
	};
	
	int main(){
		Solution s;
		int num = 14;
		bool result = s.isUgly(num);
		cout<<"Result="<<result<<endl;
		system("pause");
		return 0;
	}
	


# Note
Recursion is used to the problem.
