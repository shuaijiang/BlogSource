title: LeetCode Decode Ways
date: 2015-07-22 13:02:07
tags: leetcode
---


# Description
A message containing letters from A-Z is being encoded to numbers using the following mapping:

	'A' -> 1
	'B' -> 2
	...
	'Z' -> 26

Given an encoded message containing digits, determine the total number of ways to decode it.

For example,
Given encoded message "12", it could be decoded as "AB" (1 2) or "L" (12).

The number of ways decoding "12" is 2.

The original problem is [here](https://leetcode.com/problems/decode-ways/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/DecodeWays.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Decode Ways
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<string>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int numDecodings(string s) {
	        int size = s.size();
			vector<int> nums(size, 0);
	        if(size<=0)
	        	return 0;
	    	
			if(s[0]=='0')
	    		return 0;
	    	else
	    		nums[0] = 1;
	        
			if(size==1)
				return nums[size-1];
	        
	        if(s[1]=='0'){
				if(s[0] <= '2')
					nums[1] = 1;
				else
					return 0;
	        }
	        else{
	        	if(s[0] == '1') nums[1] = 2;
		        if(s[0] == '2'){
		        	if(s[1] <= '6') 
						nums[1]=2;
		        	else
						nums[1] = 1;
		        }
				if(s[0] >= '3') nums[1] = 1;
	        }
	        
			for(int i=2;i<size;i++){
				if(s[i] == '0'){
					nums[i] = nums[i-2];
					if(s[i-1] >= '3' || s[i-1] <= '0')
						return 0;
				}
				else{
					if(s[i-1] == '1')
						nums[i] = nums[i-1] + nums[i-2];
					else if(s[i-1] == '2') {
						if(s[i] <= '6')
							nums[i] = nums[i-1] + nums[i-2];
						else
							nums[i] = nums[i-1];
					}
					else{
						nums[i] = nums[i-1];
					}
				}
			}
			return nums[size-1];
	    }
	};

# Note
For the problem, note the zeros. If the current char is '0', we need to verify whether it is valid or not. A vecotr nums is used to save the decode ways from the begin to the current char. If the current char can be a valid letter itself and also can join with the last char, then the decode ways of the current is nums[i-1] + nums[i-2].   
