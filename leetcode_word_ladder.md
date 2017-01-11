title: LeetCode Word Ladder
date: 2015-08-13 13:32:19
tags: leetcode
---

# Description
Given two words (beginWord and endWord), and a dictionary, find the length of shortest transformation sequence from beginWord to endWord, such that:

1. Only one letter can be changed at a time
1. Each intermediate word must exist in the dictionary

For example,

Given:
start = "hit"
end = "cog"
dict = ["hot","dot","dog","lot","log"]
As one shortest transformation is "hit" -> "hot" -> "dot" -> "dog" -> "cog",
return its length 5.

The original problem is [here](https://leetcode.com/problems/word-ladder/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/WordLadder.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Word Ladder
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<string.h>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int ladderLength(string beginWord, string endWord, unordered_set<string>& wordDict) {
	        map<string, int> wordVisited;
	        queue<string> curr;
	        bool found = false;
	        int len = 0;
	        curr.push(beginWord);
	        while(!curr.empty() && !found){
	        	len ++;
	        	queue<string> next;
	        	while(!curr.empty() && !found){
	        		string str = curr.front();
	        		curr.pop();
	        		for(int i=0;i<str.size();i++){
	        			for(char ch='a';ch<='z';ch++){
	        				if(ch == str[i])
	        					continue;
	        				swap(ch, str[i]);
	        				if(str == endWord){
	        					found = true;
	        					break;
	        				}
	        				if(wordDict.count(str)>0 && wordVisited.find(str) == wordVisited.end()){
	        					wordVisited[str] = 1;
	        					next.push(str);
	        				}
	        				
	        				swap(str[i], ch);
	        			}
	        		}
	        	}
	        	curr = next;
	        }
	        if(found)
	        	return len+1;
	        else
	        	return 0;
	    }
	};

# Note
To solve the problem, width-first search was used. 
