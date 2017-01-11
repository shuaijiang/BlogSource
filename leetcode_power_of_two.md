title: LeetCode Power Of Two
date: 2015-07-07 18:33:27
tags: leetcode
---



# Description
Given an integer, write a function to determine if it is a power of two.

The original problem is [here](https://leetcode.com/problems/power-of-two/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/PowerOfTwo.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	
	/*
	*Power of Two
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	
	#include<iostream>
	#include<vector>
	#include <unordered_set>
	#include<string.h>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    bool isPowerOfTwo(int n) {
	        if(n<=0)
	        	return false;
	        if(n==1)
	        	return true;
			while(n>2&&n%2==0){
	        	if(n%2==0)
	        		n=n/2;
	        	else
	        		return false;
	        }
	        
	        if(n%2==0)
	        	return true;
	        else
	        	return false;
	    }
	};


# Note
The input integer n must larger than zero. If n is equal to 1, return true.   
