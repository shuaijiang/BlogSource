title: LeetCode Longest Palindromic Substring
date: 2015-07-26 15:18:40
tags: leetcode
---

# Description
Given a string S, find the longest palindromic substring in S. You may assume that the maximum length of S is 1000, and there exists one unique longest palindromic substring.

The original problem is [here](https://leetcode.com/problems/longest-palindromic-substring/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/LongestPalindromicSubstring.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Longest Palindromic Substring 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<string.h>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
		string longestPalindrome(string s) {
			int len = s.length();
			if(len <= 1)
	        	return s;
	        string str;
			int maxLen = 0;
			bool p[1000][1000] = {0};
			
			for(int i=len-1;i>=0;i--){
				for(int j=i;j<len;j++){
					if(s[i] == s[j] && (j-i<=2 || p[i+1][j-1])){
						p[i][j] = true;
						int sublen = j - i +1;
						if(sublen > maxLen){
							str = s.substr(i,sublen);
							maxLen = sublen;
						}
					}
					else
						p[i][j] = false;
				}
			}
			return str;
		}
	};
	
	int main(){
		string str("aaabaaaa");
		Solution s;
		cout<<"str="<<str<<endl;
		//string new_str = s.inverse(str);
		//cout<<"new str="<<new_str<<endl;
		//cout<<"isPalindrome="<<s.isPalindrome(str);
		string substr = s.longestPalindrome(str);
		cout<<"substr="<<substr<<endl;
	}

# Note
To solve the problem, dynamic program is used. P[i][j] labels whether the substr(i,j) is palindrome or not.
