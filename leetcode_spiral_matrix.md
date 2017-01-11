title: LeetCode Spiral Matrix 
date: 2015-07-21 10:21:24
tags: leetcode
---

# Description
Given a matrix of m x n elements (m rows, n columns), return all elements of the matrix in spiral order.

For example,
Given the following matrix:
	
	[
	 [ 1, 2, 3 ],
	 [ 4, 5, 6 ],
	 [ 7, 8, 9 ]
	]

You should return [1,2,3,6,9,8,7,4,5].

The original problem is [here](https://leetcode.com/problems/spiral-matrix/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/SpiralMatrix.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Spiral Matrix 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	using namespace std;
	
	class Solution {
	public:
	    vector<int> spiralOrder(vector<vector<int>>& matrix) {
	        int rowBegin, rowEnd;
			int colBegin, colEnd;
			vector<int> result;
			int rowSize = matrix.size();
			if(rowSize<=0)
				return result;
				
			int colSize = matrix[0].size();
			if(colSize<=0)
				return result;
			
			rowBegin = 0; rowEnd = rowSize-1;
			colBegin = 0; colEnd = colSize-1;
			while(rowBegin<rowEnd && colBegin<colEnd) {
				for(int i=colBegin;i<colEnd;i++)
					result.push_back(matrix[rowBegin][i]);
				for(int i=rowBegin;i<rowEnd;i++)
					result.push_back(matrix[i][colEnd]);
				for(int i=colEnd;i>colBegin;i--)
					result.push_back(matrix[rowEnd][i]);
				for(int i=rowEnd;i>rowBegin;i--)
					result.push_back(matrix[i][colBegin]);
				rowBegin ++; rowEnd --;
				colBegin ++; colEnd --;
			}
			if(rowBegin == rowEnd && colBegin == colEnd)
				result.push_back(matrix[rowBegin][colBegin]);
			else{
				if(rowBegin == rowEnd){
					for(int i=colBegin;i<=colEnd;i++)
						result.push_back(matrix[rowBegin][i]);
				}
				if(colBegin == colEnd){
					for(int i=rowBegin;i<=rowEnd;i++)
						result.push_back(matrix[i][colBegin]);
				}
			}
			return result;
	    }
	};

# Note
To solve the problem, four anchors are needed: rowBegin, rowEnd, colBegin, colEnd. The order I traveral the matrix: rowBegin, colEnd, rowEnd, colBegin. In the end, only one row or one column is remained, then traversal it.  
