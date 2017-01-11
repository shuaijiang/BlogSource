title: LeetCode Roman To Integer
date: 2015-07-26 18:37:24
tags: leetcode
---
# Description
Given a roman numeral, convert it to an integer.

Input is guaranteed to be within the range from 1 to 3999.

The original problem is [here](https://leetcode.com/problems/roman-to-integer/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/RomanToInteger.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Roman to Integer 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<string.h>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int romanToInt(string s) {
	    	int len = s.size();
	    	if(len<=0)
	    		return 0;
	        char roman[] = {'I','V','X','L','C','D','M'};
	        int  myInt[] = {1,5,10,50,100,500,1000};
	        map<char, int> romanMap;
	        for(int i=0;i<7;i++)
	        	romanMap[roman[i]] = myInt[i];
			int result = 0;
			result += romanMap[s[0]];
			char lastCh = s[0];
			for(int i=1;i<len;i++){
				if(romanMap[lastCh] < romanMap[s[i]]){
					result = result - 2*romanMap[lastCh] + romanMap[s[i]];
					lastCh = s[i];
				}
				else{
					result = result + romanMap[s[i]];
					lastCh = s[i];
				}
			}
			return result;
	    }
	};

# Note
To solve the problem, first map all the roman to integer. If the integer of current roman is lager than the last roman, then add the integer to the result, else minus the 2*integer of the last roman, and plus the integer of current roman. 
