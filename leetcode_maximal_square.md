title: LeetCode Maximal Square
date: 2015-08-05 10:12:04
tags: leetcode
---

# Description
Given a 2D binary matrix filled with 0's and 1's, find the largest square containing all 1's and return its area.

For example, given the following matrix:

	1 0 1 0 0
	1 0 1 1 1
	1 1 1 1 1
	1 0 0 1 0
Return 4.

The original problem is [here](https://leetcode.com/problems/maximal-square/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/MaximalSquare.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Maximal Square
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int maximalSquare(vector<vector<char>>& matrix) {
	        int rowNum = matrix.size();
	        if(rowNum <= 0)
	        	return 0;
	        int colNum = matrix[0].size();
	        vector<int> oneRow(colNum, 0);
	        vector<vector<int>> dp;
	        for(int i=0;i<rowNum;i++)
	        	dp.push_back(oneRow);
	    	int sideLength = 0;
	    	// get the maximum side length
	        for(int i=0;i<rowNum;i++){
	        	for(int j=0;j<colNum;j++){
	        		dp[i][j] = matrix[i][j] - '0';
	        		if(i-1=>0 && j-1=>0 && dp[i][j]>0){
	        			dp[i][j] = min(dp[i-1][j-1], min(dp[i-1][j], dp[i][j-1])) + 1;
	        		}
	        		if(dp[i][j] > sideLength)
	        			sideLength = dp[i][j];
	        	}
	        }
	        return sideLength * sideLength;
	    }
	};

# Note
To solve the problem, I use dynamic program and save the maximal side length of the square. 
