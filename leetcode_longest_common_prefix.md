title: LeetCode Longest Common Prefix
date: 2015-04-03 14:44:50
tags: leetcode
---

# Description
Write a function to find the longest common prefix string amongst an array of strings.

The original problem is [here](https://leetcode.com/problems/longest-common-prefix/ "Problem").
The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/LongestCommonPrefix.cpp "Code").

<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Longest Common Prefix 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stringstream>
	using namespace std;
	
	class Solution {
	public:
	    string longestCommonPrefix(vector<string> &strs) {
	        int vec_len = strs.size();
			string strPrefix ;
			if(vec_len > 0)
			{
				vector<string>::iterator iter;
				iter=strs.begin();
				strPrefix = *iter;
				for(iter=strs.begin();iter<strs.end();++iter)
		        {
		        	strPrefix = commonPrefix(strPrefix,*iter);
		        }
			} 
			else
			{
				strPrefix = "";
			}
	
	        return strPrefix;
	    }
	    string commonPrefix(string str1, string str2)
		{
			int len = str1.size()>str2.size() ? str2.size(): str1.size();
			string strPrefix;
			for(int count=0;count<len;++count)
			{
				if(str1[count] == str2[count])
				{
					stringstream ss;
					string str_ch;
					ss.clear();
					ss<<str1[count];
					ss>>str_ch;
					strPrefix.append(str_ch);	
				}
				else
					break;
			}
			return strPrefix;
		} 
	};

# Note
The method is similar to compute the minimal or maximal value of one integer array. The only different is in this problem the element is string instead of integer. Additionally, we need get the common prefix of two string. 
