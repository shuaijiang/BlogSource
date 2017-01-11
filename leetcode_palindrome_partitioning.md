title: LeetCode Palindrome Partitioning
date: 2015-08-13 10:43:29
tags: leetcode
---

# Description
Given a string s, partition s such that every substring of the partition is a palindrome.

Return all possible palindrome partitioning of s.

For example, given s = "aab",
Return
	
	  [
	    ["aa","b"],
	    ["a","a","b"]
	  ]

The original problem is [here](https://leetcode.com/problems/palindrome-partitioning/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/PalindromePartitioning.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Palindrome Partitioning 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<string.h>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    vector<vector<string>> partition(string s) {
	        vector<vector<string>> result;
	        int len = s.length();
			if(len <= 0)
				return result;
			vector<string> path;
	        dfs(s, path, result, 0, 1);
	        return result;
	    }
	    void dfs(string &s, vector<string> &path, vector<vector<string>> &result, int prev, int start){
			if(start == s.size()){
				if(isPalindrome(s, prev, start-1)){
					path.push_back(s.substr(prev, start-prev));
					result.push_back(path);
					path.pop_back();
				}
				return;
			}
			dfs(s, path, result, prev, start+1);
			if(isPalindrome(s, prev, start-1)){
				path.push_back(s.substr(prev, start-prev));
				dfs(s, path, result, start, start+1);
				path.pop_back();			
			}
			return;
	    }
	    bool isPalindrome(string & s, int start, int end){
	    	while(s[start] == s[end]){
	    		start ++;
	    		end --;
	    	}
	    	if(start < end)
	    		return false;
	    	else
	    		return true;
	    }
	};

# Note
To solve the problem, depth-first search was used. 
