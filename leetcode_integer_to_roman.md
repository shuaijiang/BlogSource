title: LeetCode Integer To Roman
date: 2015-08-13 09:28:23
tags: leetcode
---

# Description
Given an integer, convert it to a roman numeral.

Input is guaranteed to be within the range from 1 to 3999.

The original problem is [here](https://leetcode.com/problems/integer-to-roman/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/IntegerToRoman.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Integer to Roman
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<string.h>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    string intToRoman(int num) {
	        int radix[] = {1000,900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
	        string symbol[] = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
	        string roman;
	        for(int i=0;num>0;i++){
	        	int count = num / radix[i];
	        	num =  num % radix[i];
	        	while(count>0){
	        		roman += symbol[i];
	        		count--;
	        	}
	        }
	        return roman;
	    }
	};

# Note
To solve the problem, the num was divided by the radix from 1000 to 1, and the num was assigned by the remainder. The roman was joint with the symbol.
