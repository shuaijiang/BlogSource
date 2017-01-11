title: LeetCode Remove Element
date: 2015-04-03 11:22:16
tags: leetcode
---


# Description
Given an array and a value, remove all instances of that value in place and return the new length.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

The original problem is [here](https://leetcode.com/problems/remove-element/ "Problem").
The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/RemoveElement.cpp "Code").

<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Remove Element
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	
	class Solution {
	public:
	    int removeElement(int A[], int n, int elem) {
			int new_len = 0;
			for(int count=0;count<n;++count)
	        {
	        	if(A[count] != elem)
	        	{
	        		A[new_len] = A[count];
	        		new_len ++;	
	        	}
	        }
	        return new_len;
	    }
	};


# Note
Just keep patient!
