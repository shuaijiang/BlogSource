title: LeetCode Isomorphic Strings
date: 2015-06-25 22:33:02
tags: leetcode
---

# Description
Given two strings s and t, determine if they are isomorphic.

Two strings are isomorphic if the characters in s can be replaced to get t.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character but a character may map to itself.

For example,
Given "egg", "add", return true.

Given "foo", "bar", return false.

Given "paper", "title", return true.

Note:
You may assume both s and t have the same length.

The original problem is [here](https://leetcode.com/problems/isomorphic-strings/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/IsomorphicStrings.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Isomorphic Strings 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	
	#include<iostream>
	#include<vector>
	#include<map>
	#include<string.h>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    bool isIsomorphic(string s, string t) {
	    	if(s == t)
	    		return true;
	        map<char,int> mapS, mapT;
	        vector<int>   vectorS,vectorT;
	        int countS=0,countT=0;
	        for(int count=0;count<s.length();++count){
	        	if(mapS.find(s[count]) == mapS.end()){
	        		mapS[s[count]] = countS;
	        		vectorS.push_back(countS);
	        		countS ++;
	        	}
	        	else{
	        		vectorS.push_back(mapS[s[count]]);
	        	}
	        }
	        for(int count=0;count<t.length();++count){
	        	if(mapT.find(t[count]) == mapT.end()){
	        		mapT[t[count]] = countT;
	        		vectorT.push_back(countT);
	        		countT ++;
	        	}
	        	else{
	        		vectorT.push_back(mapT[t[count]]);
	        	}
	        }
	        
	        for(int count=0;count<vectorS.size();++count){
	        	//cout<<"S="<<vectorS[count]<<" "<<"T="<<vectorT[count]<<endl;
	        	if(vectorS[count] != vectorT[count])
	        		return false;
	        }
	        return true;
	    }
	};
	//The code under below is used for test
	int main(){
		Solution solution;
		string s("ab"), t("ac");
		bool isIs = solution.isIsomorphic(s,t);
		cout<<"isIs="<<isIs<<endl;
		system("pause");
		return 0;
	}

# Note
To solve the problem, I map the characters to intergers, and save the map in a hash(map in C++). The first character appears in the string is convert to 0, if the second character is not in the hash, then is convert to 1, else map to the intergers in the hash. Doing the upper steps, until to the end of the string. Then, we just compare the intergers sequences of the two strings, if they are the same, then return true, else return false.
