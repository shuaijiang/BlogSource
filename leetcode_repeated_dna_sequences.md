title: LeetCode Repeated DNA Sequences
date: 2015-08-10 23:26:56
tags: leetcode
---

# Description

All DNA is composed of a series of nucleotides abbreviated as A, C, G, and T, for example: "ACGAATTCCG". When studying DNA, it is sometimes useful to identify repeated sequences within the DNA.

Write a function to find all the 10-letter-long sequences (substrings) that occur more than once in a DNA molecule.

For example,

	Given s = "AAAAACCCCCAAAAACCCCCCAAAAAGGGTTT",
	
	Return:
	["AAAAACCCCC", "CCCCCAAAAA"].

The original problem is [here](https://leetcode.com/problems/repeated-dna-sequences/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/RepeatedDNASequences.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Repeated DNA Sequences
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<map>
	#include<stdlib.h>
	#define Code 0x3ffff 
	using namespace std;
	
	class Solution {
	public:
	    vector<string> findRepeatedDnaSequences(string s) {
	        int size = s.size();
	        vector<string> res;
	        if(size <= 10)
	        	return res;
	        map<int, int> myMap;
	        map<char, int> char2int;
	        char2int['A'] = 0;
	        char2int['C'] = 1;
	        char2int['G'] = 2;
	        char2int['T'] = 3;
	        int strInt = 0;
	        for(int i=0;i<10;i++){
	        	strInt = (strInt << 2) + char2int[s[i]];
	        }
	        myMap[strInt] = 1;
	        
			for(int i=10; i<size; i++){
				strInt = ((strInt & Code) << 2) + char2int[s[i]];
	        	if(myMap.find(strInt) == myMap.end())
	        		myMap[strInt] = 1;
	        	else{
	        		if(myMap[strInt] == 1){
	        			string substr = s.substr(i-9,10);
	        			res.push_back(substr);
	        		}
	        		myMap[strInt] ++;
	        	}
	        }
	        return res;
	    }
	};
	

# Note
To solve the problem, use a map to save the 10-letter-long sequences and the frequence of it. Put the sequences with more than 1 frequence to the result.

However, this solution lead to 'Memory Limit Exceeded', to solve the problem, convert the 10-letter-long substring to an integer with 'A' represent '00', 'C' represent '01', 'G' represent '10', 'T' represent '11'.  
