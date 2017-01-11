title: LeetCode Sqrt(x)
date: 2015-07-09 10:22:47
tags: leetcode
---


# Description

Given two binary trees, write a function to check if they are equal or not.

Two binary trees are considered equal if they are structurally identical and the nodes have the same value.

The original problem is [here](https://leetcode.com/problems/sqrtx/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/Sqrt\(x\).cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*Sqrt(x) 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int mySqrt(int x) {
	    	if(x <= 0)
	    		return -1;
	        if(x == 1)
	        	return 1;
	        
	        int low  = 1;
	        int high = x/2+1;
	        int mid;
	        while(low<=high){
	        	mid = (low+high)/2;
				 
	        	if(mid <= x/mid  && (mid+1) > x/(mid+1))
	        		return mid;
	        	else if(mid > x/mid)
	        		high -= 1;
	        	else
	        		low += 1;
	        }
	        return -1;
	    }
	};


# Note
To solve the problem, binary search is needed.
