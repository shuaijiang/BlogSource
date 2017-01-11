title: LeetCode Anagrams
date: 2015-08-02 20:47:58
tags: leetcode
---


# Description
Given an array of strings, return all groups of strings that are anagrams.

Note: All inputs will be in lower-case.

The original problem is [here](https://leetcode.com/problems/anagrams/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/Anagrams.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Anagrams
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
	    vector<string> anagrams(vector<string>& strs) {
	        int size = strs.size();
	        map<string, int> myMap;
			vector<string> result;
			if(size <= 0)
				return result;
				
	        for(int i=0;i<size;i++){
				string str = strs[i];
				sort(str.begin(),str.end());
				if(myMap.find(str) == myMap.end()){
					myMap[str] = i;
				}
				else{
					if(myMap[str] >= 0){
						result.push_back(strs[myMap[str]]);
						myMap[str] = -1;
					}
					result.push_back(strs[i]);
				}
	        }
	        return result;
	    }
	};

# Note
To solve the problem, save each new sorted string to the map, the key is the string, the value is its index. If two strings are anagrams, their sorted strings are the same. We can find the same sorted string, and push them in the vector.  
