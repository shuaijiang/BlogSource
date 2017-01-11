title: LeetCode Unique Paths
date: 2015-07-12 10:22:27
tags: leetcode
---

# Description
A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?

The original problem is [here](https://leetcode.com/problems/unique-paths/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/UniquePaths.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Unique Paths 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int uniquePaths(int m, int n) {
	        int matrix[100][100];
	        matrix[0][0] = 1;
	        for(int i=1;i<n;i++)
	        	matrix[0][i]=1;
	        for(int j=1;j<m;j++)
	        	matrix[j][0] = 1;
	        for(int i=1;i<m;i++){
	        	for(int j=1;j<n;j++){
	        		matrix[i][j] = matrix[i-1][j] + matrix[i][j-1];
	        	}
	        }
	        return matrix[m-1][n-1];
	    }
	};


# Note
Dynamic programming is used. The number of paths to get (i,j) in grid is equal to the sum of  the result of (i,j-1) and (i-1,j).
