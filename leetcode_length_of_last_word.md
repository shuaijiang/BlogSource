title: LeetCode Length Of Last Word
date: 2015-06-25 19:03:35
tags: leetcode
---



# Description
Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string.

If the last word does not exist, return 0.

Note: A word is defined as a character sequence consists of non-space characters only.

For example, 
Given s = "Hello World",
return 5.

The original problem is [here](https://leetcode.com/problems/length-of-last-word/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/LengthOfLastWord.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Length of Last Word
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<string.h>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int lengthOfLastWord(string s) {
	    	if(s==" " || s=="")
	    		return 0;
	    	s = filter(s);
	    	int spaceIndex=-1;
	    	int len = s.length();
	    	for(int count=0;count<len-1;++count){
	    		if(s[count] == ' '){
	    			spaceIndex = count;
	    		}
	    	}
	    	if(spaceIndex == -1)
	    		return len;
	    	int wordLen = len - 1 - spaceIndex;
	    	return wordLen;
	    }
	    //Remove the space at the begining or end of the string
	    string filter(string s){
	    	string str;
	    	int begin = 0, end=s.length()-1;
	    	while(s[begin] == ' '){
	    		begin ++;
	    	}
	    	while(s[end] == ' '){
	    		end --;
	    	} 
	    	for(int count=begin;count<=end;count++){    		
				str.push_back(s[count]);
	    	}
	    	return str;
	    }
	    
	};



# Note
To solve the problem, first remove all the spaces at the begining or end of the string. Then, find the space which nearest to the end of the string. So, we can compute the length from the space to the end. If we don't find the space, return the length of the string.
