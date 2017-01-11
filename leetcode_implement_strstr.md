title: LeetCode Implement strStr
date: 2015-07-12 23:11:18
tags: leetcode
---


# Description

The original problem is [here](https://leetcode.com/problems/implement-strstr/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ImplementStrStr.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Implement strStr()  
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int strStr(string haystack, string needle) {
			int i, j;
	        for (i = j = 0; i < haystack.size() && j < needle.size();) {
	        	if (haystack[i] == needle[j]){
	            	++i; ++j;
	            }
	        	else{
	        		i -= j - 1; j = 0;
	        	}
	        }
	        return j != needle.size() ? -1 : i - j;
	    }
	};


# Note
Traversal the haystack, and find whether the substring is match to needle. 
