title: LeetCode Word Break
date: 2015-06-25 21:34:22
tags: leetcode
---




# Description
Given a string s and a dictionary of words dict, determine if s can be segmented into a space-separated sequence of one or more dictionary words.

For example, given
s = "leetcode",
dict = ["leet", "code"].

Return true because "leetcode" can be segmented as "leet code".

The original problem is [here](https://leetcode.com/problems/word-break/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/WordBreak.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Word Break
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	
	#include<iostream>
	#include<vector>
	#include <unordered_set>
	#include<string.h>
	#include<stdlib.h>
	using namespace std;
	class Solution {
	public:
	    bool wordBreak(string s, unordered_set<string>& wordDict) {
	        if(wordDict.find(s)!=wordDict.end())
	        	return true;
	        vector<int> wordIndex;
			int sublen = 0, subBegin = 0, subEnd = 0;
	        string substr;
	        wordIndex.push_back(-1);
			for(int count=0;count<s.length();++count){
				for(int i=0;i<wordIndex.size();i++){
					subBegin = wordIndex[i]+1;
					sublen = count - subBegin + 1;
		        	substr = s.substr(subBegin,sublen);
					if(wordDict.find(substr)!=wordDict.end()){
						wordIndex.push_back(count);
						break;
					}
				}
	        }
	        int len = wordIndex.size();
	        if(wordIndex[len-1] == s.length()-1)
				return true;
			else
	        	return false;
	    }
	};

# Note
To solve the problem, I use a vector to save the index(i) of string, which means from begin to i, the substring can be segmented as one or more word in the dictionary. Traverse the string and judge if the substring from any index in the vector to the current index is in the dictionary. If so, put the current to the vector and go on until the end of the string.
Finally, if the index of the end of string is in the vector, we can say the string can be segmented successfully, else return false.
