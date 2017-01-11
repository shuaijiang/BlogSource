title: LeetCode Unique Paths2
date: 2015-07-12 23:28:43
tags: leetcode
---

# Description
Follow up for "Unique Paths":

Now consider if some obstacles are added to the grids. How many unique paths would there be?

An obstacle and empty space is marked as 1 and 0 respectively in the grid.

For example,
There is one obstacle in the middle of a 3x3 grid as illustrated below.

	[
	  [0,0,0],
	  [0,1,0],
	  [0,0,0]
	]
The total number of unique paths is 2.

The original problem is [here](https://leetcode.com/problems/unique-paths-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/UniquePaths2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Unique Paths 2
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
	        int matrix[100][100];
	        int rowSize=obstacleGrid.size();
	        if(rowSize<=0)
	        	return 0;
	        vector<int>oneRow = obstacleGrid[0];
	        int colSize = oneRow.size();
	        if(obstacleGrid[0][0]==0)
	        	matrix[0][0] = 1;
	        else
	        	matrix[0][0] = 0;
	        for(int i=1;i<colSize;i++){
	        	if(obstacleGrid[0][i]==1)
	        		matrix[0][i] = 0;
	        	else
	        		matrix[0][i] = matrix[0][i-1];
	        }
	        for(int j=1;j<rowSize;j++){
	        	if(obstacleGrid[j][0]==1)
	        		matrix[j][0] = 0;
	        	else
	        		matrix[j][0] = matrix[j-1][0];
	        }
	        
	        for(int i=1;i<rowSize;i++){
	        	for(int j=1;j<colSize;j++){
	        		if(obstacleGrid[i][j]==1)
	        			matrix[i][j] = 0;
	        		else
	        			matrix[i][j] = matrix[i-1][j] + matrix[i][j-1];
	        	}
	        }
	        return matrix[rowSize-1][colSize-1];
	    }
	};


# Note
Dynamic programming is used. The number of paths to get (i,j) in grid is equal to the sum of matrix(i,j-1) and matrix(i-1,j). However, if the grid(i,j) is equal to 1, set matrix(i,j) = 0.
