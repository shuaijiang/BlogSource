title: LeetCode Valid Palindrome
date: 2015-06-25 16:02:42
tags: leetcode
---

# Description
Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

For example,
"A man, a plan, a canal: Panama" is a palindrome.
"race a car" is not a palindrome.

The original problem is [here](https://leetcode.com/problems/valid-palindrome/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ValidPalindrome.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Valid Palindrome
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
	    bool isPalindrome(string s) {
	    	s = filter(s);
			if(s.size() <=1)
				return true;
	        int len = s.length();
	        for(int count=0;count<len/2;count++){
	        	if(s[count] != s[len-count-1])
	        		return false;
	        }
	        return true;
	    }
	    
	    string filter(string s){
	    	if(s == "")
	    		return s;
			int len = s.length();
			string str;
			for(int count=0;count<len;++count){
				char  ch = s[count];
				if(ch>='A'&&ch<='Z')
					str.push_back(ch+32);
				else if((ch>='a'&&ch<='z') || (ch>='0'&&ch<='9'))
					str.push_back(ch);
			}
			return str;
	    }
	};
	//The codes under below is used for test
	int main(){
		string str("aa");
		Solution s;
		string filter_str = s.filter(str);
		cout<<"Filter="<<filter_str<<endl;
		bool isP = s.isPalindrome(str);
		cout<<"isPalindrome="<<isP<<endl;
		system("pause");
		return 0;
	}



# Note
To solve the problem, first we should filter the string except alphanumeric characters. Then, we can compare the characters the two point of the string.
