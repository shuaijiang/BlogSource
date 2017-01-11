title: LeetCode Search A 2D Matrix 2
date: 2015-07-23 09:34:36
tags: leetcode
---

# Description
Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:

Integers in each row are sorted in ascending from left to right.
Integers in each column are sorted in ascending from top to bottom.
For example,

Consider the following matrix:
	
	[
	  [1,   4,  7, 11, 15],
	  [2,   5,  8, 12, 19],
	  [3,   6,  9, 16, 22],
	  [10, 13, 14, 17, 24],
	  [18, 21, 23, 26, 30]
	]
Given target = 5, return true.

Given target = 20, return false.

The original problem is [here](https://leetcode.com/problems/search-a-2d-matrix-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/SearchA2DMatrix2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Search a 2D Matrix 2
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    bool searchMatrix(vector<vector<int>>& matrix, int target) {
	        int rowSize = matrix.size();
	        if(rowSize <= 0)
	        	return false;
	        vector<int> oneRow = matrix[0];
	        int colSize = oneRow.size();
	        if(colSize<=0)
	        	return false;
	        
	        int coli = 0, colj = colSize -1;
	        int maxCol;
	        while(coli<=colj){
	        	maxCol = colj;
	        	int middle = (coli+colj)/2;
	        	if(matrix[0][middle] == target)
	        		return true;
	        	else if(matrix[0][middle] < target)
	        		coli = middle + 1;
	        	else
	        		colj = middle - 1;
	        }
	        
	        for(int i=0;i<=maxCol;i++){
	        	if(matrix[0][i]==target)
	        		return true;
	        	else if(matrix[0][i]<target){
	        		int rowi=0, rowj=rowSize-1;
					while(rowi<=rowj){
						int middle = (rowi+rowj)/2;
						if(matrix[middle][i] == target)
			        		return true;
			        	else if(matrix[middle][i] < target)
			        		rowi = middle + 1;
			        	else
			        		rowj = middle - 1;
					}
	        	}
	        	else
	        		break;
	        }
	        return false;
	    }
	};

# Note
First, find all the columns which the first elements of the columns are less than or equal to the target. We use binary search to find them.

Second, for these columns, use binary search to find the target.
