title: LeetCode Search A 2D Matrix
date: 2015-07-19 23:00:08
tags: leetcode
---

# Description
Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:

Integers in each row are sorted from left to right.
The first integer of each row is greater than the last integer of the previous row.
For example,

Consider the following matrix:

	[
	  [1,   3,  5,  7],
	  [10, 11, 16, 20],
	  [23, 30, 34, 50]
	]

Given target = 3, return true.

The original problem is [here](https://leetcode.com/problems/search-a-2d-matrix/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/SearchA2DMatrix.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Search a 2D Matrix  
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	using namespace std;
	
	class Solution {
	public:
	    bool searchMatrix(vector<vector<int>>& matrix, int target) {
	        int rowSize = matrix.size();
	        if(rowSize <= 0)
	        	return false;
	        vector<int> oneRow = matrix[0];
	        int colSize = oneRow.size();
	        int rowTarget = -1;
	        for(int i=0;i<rowSize;i++){
	        	if(target <= matrix[i][colSize-1]){
	        		rowTarget = i;
	        		break;
	        	}
	        }
	    	if(rowTarget == -1)
	    		return false;
	    	for(int i=0;i<colSize;i++){
	    		if(target == matrix[rowTarget][i]){
	    			return true;
	    		}
	    	}
	    	return false;
	    }
	};	


# Note
First, judge which row this target belongs to; and then traversal this row to judge whether the target is in this row or not.
