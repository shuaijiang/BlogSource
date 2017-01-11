title: LeetCode Substring with Concatenation of All Words
date: 2015-08-18 22:10:54
tags: leetcode
---


# Description
You are given a string, s, and a list of words, words, that are all of the same length. Find all starting indices of substring(s) in s that is a concatenation of each word in words exactly once and without any intervening characters.

For example, given:
s: "barfoothefoobarman"
words: ["foo", "bar"]

You should return the indices: [0,9].
(order does not matter).

The original problem is [here](https://leetcode.com/problems/substring-with-concatenation-of-all-words/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/SubstringWithConcatenationOfAllWords.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Substring with Concatenation of All Words 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    vector<int> findSubstring(string s, vector<string>& words) {
	        vector<int> result;
	        int wordsNum = words.size();
			if(wordsNum <= 0)
				return result;
			int wordLen = words[0].size();
			int strLen  = s.size();
			if(strLen <= 0 || strLen < wordLen)
				return result;
			
			map<string, int> wordMap;
			for(int i=0;i<wordsNum;i++)
				++ wordMap[words[i]];
			
			int subLen = wordsNum * wordLen; 
			for(int i=0;i<=strLen - subLen;i++){
				map<string, int> myMap(wordMap);
				for(int j=i;j<i+subLen;j+=wordLen){
					string substr = s.substr(j,wordLen);
					if(myMap.find(substr) != myMap.end()){
						myMap[substr] --;
						if(myMap[substr] == 0)
							myMap.erase(substr);
					}					
					else
						break;
				}
				if(myMap.size() == 0)
					result.push_back(i);
			}
			return result;
	    }
	};



# Note
In the solution, we need traversal the string. And, map is used to save the dictionary. If a substring is consisted of all the words in the dictionary, we get one answer.
