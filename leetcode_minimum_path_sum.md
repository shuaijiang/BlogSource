title: LeetCode Minimum Path Sum
date: 2015-07-14 21:07:26
tags: leetcode
---

# Description
Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.

The original problem is [here](https://leetcode.com/problems/minimum-path-sum/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/MinimumPathSum.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Minimum Path Sum
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<math>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int minPathSum(vector<vector<int>>& grid) {
	        int rowSize = grid.size();
	        if(rowSize<=0)
	        	return 0;
	        vector<int> oneRow = grid[0];
	        int colSize = oneRow.size();
	        
	        int **matrix = new int*[rowSize];
	        for(int i=0;i<rowSize;i++){
	        	matrix[i] = new int[colSize];
	        	for(int j=0;j<colSize;j++)
	        		matrix[i][j] = 0;
	        }
	    	matrix[0][0] = grid[0][0];
	    	for(int i=1;i<colSize;i++)
	        	matrix[0][i] = matrix[0][i-1] + grid[0][i];
	        for(int i=1;i<rowSize;i++)
	        	matrix[i][0] = matrix[i-1][0] + grid[i][0];
	        
	        for(int i=1;i<rowSize;i++){
	        	for(int j=1;j<colSize;j++){
	        		matrix[i][j] = grid[i][j] + min(matrix[i-1][j],matrix[i][j-1]);
	        	}
	        }
	        return matrix[rowSize-1][colSize-1];
	    }
	};

# Note
To get the minimum path, I use a matrix to record the sum of every step. For every step, always choose the minimum step(down or right). 
