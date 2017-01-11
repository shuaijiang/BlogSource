title: LeetCode Valid Anagram
date: 2015-08-01 20:34:57
tags: leetcode
---

# Description
Given two strings s and t, write a function to determine if t is an anagram of s.

For example,
s = "anagram", t = "nagaram", return true.
s = "rat", t = "car", return false.

Note:
You may assume the string contains only lowercase alphabets.

The original problem is [here](https://leetcode.com/problems/valid-anagram/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ValidAnagram.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Valid Anagram 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<string>
	#include<map> 
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    bool isAnagram(string s, string t) {
	        int size1 = s.size();
	        int size2 = t.size();
	        map<char, int> myMap;
	        if(size1 != size2)
	        	return false;
	        if(size1 == 1 && size2 == 1) {
	        	if(s[0] == t[0])
	        		return true;
	        	else
	        		return false;
	        }
	        for(int i=0;i<size1;i++){
				if(myMap.find(s[i]) == myMap.end())
					myMap[s[i]] = 1;
				else
					myMap[s[i]] += 1;
	        }
	
	        for(int i=0;i<size1;i++){
	        	if(myMap.find(t[i]) == myMap.end())      		
	        		return false;
	        	else if(myMap[t[i]] == 0)
	        		return false;
	        	else
	        		myMap[t[i]] --;
	        }
	        return true;
	    }
	};


# Note
To solve the problem, use a map to save the count of each alphabet in string s. Then, traversal string t, and find each alphabet in the map and minus the count of it. If the alphabet does not exist in the map or the count of the alphabet is zeros, then return false. Finally, return true.
