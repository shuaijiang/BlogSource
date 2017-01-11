title: LeetCode Edit Distance
date: 2015-08-26 23:14:01
tags: leetcode
---

# Description
Given two words word1 and word2, find the minimum number of steps required to convert word1 to word2. (each operation is counted as 1 step.)

You have the following 3 operations permitted on a word:

a) Insert a character
b) Delete a character
c) Replace a character


The original problem is [here](https://leetcode.com/problems/edit-distance/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/EditDistance.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*
	*Edit Distance
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int minDistance(string word1, string word2) {
	        int size1 = word1.size();
	        int size2 = word2.size();
	        if(size1 <= 0 && size2 > 0)
	        	return size2;
	        else if(size2 <= 0 && size1>0)
	        	return size1;
	        else if(size1 <= 0 && size2 <= 0)
	        	return 0;
	        vector<vector<int> > distance(size1+1, vector<int>(size2+1,0));
	        
	        for(int i=0;i<=size1;i++)
					distance[i][0] = i;
	        for(int j=0;j<=size2;j++)
	        		distance[0][j] = j;
	        
	        for(int i=1;i<=size1;i++){
	        	for(int j=1;j<=size2;j++){
	        		if(word1[i-1] != word2[j-1])
	        			distance[i][j] = min(min(distance[i-1][j-1], distance[i-1][j]), distance[i][j-1]) + 1;
	        		else
	        			distance[i][j] = distance[i-1][j-1];
	        	}
	        }
	        return distance[size1][size2];
	    }
	};

# Note
To solve the problem, dynamic programming was used. 
