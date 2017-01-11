title: LeetCode Count And Say
date: 2015-07-01 18:27:47
tags: leetcode
---


# Description
The count-and-say sequence is the sequence of integers beginning as follows:
1, 11, 21, 1211, 111221, ...

1 is read off as "one 1" or 11.
11 is read off as "two 1s" or 21.
21 is read off as "one 2, then one 1" or 1211.
Given an integer n, generate the nth sequence.

Note: The sequence of integers will be represented as a string.

The original problem is [here](https://leetcode.com/problems/count-and-say/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/CountAndSay.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Count and Say 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<string>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    string countAndSay(int n) {
	    	if(n==0)
	    		return "";
	        if(n==1)
	        	return "1";
	        string str("1");
	        for(int i=1;i<n;i++){
	        	str = countNext(str);
	        }
	        return str;
	    }
	    string countNext(string str){
	    	int count = 1;
	    	char lastCh=str[0],countCh;
	    	string newStr;
	    	for(int i=1;i<str.length();++i){
	    		if(str[i]==lastCh){
	    			count ++;
	    		}
	    		else{
	    			countCh = '0'+count;
	    			newStr.push_back(countCh);
	    			newStr.push_back(lastCh);
	    			lastCh = str[i];
	    			count = 1;
	    		}
	    	}
	    	countCh = '0'+count;
			newStr.push_back(countCh);
			newStr.push_back(lastCh);
	    	return newStr;
	    }
	};

# Note
Just count the continous same number in the string.
