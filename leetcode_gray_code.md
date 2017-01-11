title: LeetCode Gray Code
date: 2015-07-14 11:37:48
tags: leetcode
---

# Description
The gray code is a binary numeral system where two successive values differ in only one bit.

Given a non-negative integer n representing the total number of bits in the code, print the sequence of gray code. A gray code sequence must begin with 0.

For example, given n = 2, return [0,1,3,2]. Its gray code sequence is:

	00 - 0
	01 - 1
	11 - 3
	10 - 2

The original problem is [here](https://leetcode.com/problems/gray-code/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/GrayCode.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Gray Code
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<math>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    vector<int> grayCode(int n) {
	        vector<int> result;
			if(n<0)
				return result;
			
			result.push_back(0);
			if(n==0)
				return result;
			result.push_back(1);
			if(n==1)
				return result;
			
			for(int i=2;i<=n;i++){
				int size = result.size();
				int addNum = pow(2,i-1);
				for(int j=size-1;j>=0;j--){
					int num = result[j] + addNum;
					result.push_back(num);
				}
			}
			return result;
	    }
	};

# Note
The Gray Code of n contains two parts: One part is the codes which add 0 to front of all codes of n-1; The other part is the codes which add 1 to front of all codes of n-1 in the reverse order. 

For example, when n=2, the Grad code is 

	00 - 0
	01 - 1
	11 - 3
	10 - 2

So, when n=3, the Gray code is

	000 - 0
	001 - 1
	011 - 3
	010 - 2
	
	110 - 6
	111 - 7
	101 - 5
	100 - 4
