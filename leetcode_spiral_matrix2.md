title: LeetCode Spiral Matrix 2
date: 2015-07-21 11:02:37
tags: leetcode
---


# Description
Given an integer n, generate a square matrix filled with elements from 1 to n2 in spiral order.

For example,
Given n = 3,

You should return the following matrix:
	[
	 [ 1, 2, 3 ],
	 [ 8, 9, 4 ],
	 [ 7, 6, 5 ]
	]

The original problem is [here](https://leetcode.com/problems/spiral-matrix-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/SpiralMatrix2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Spiral Matrix 2
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    vector< vector<int> > generateMatrix(int n) {
	        vector< vector<int> > matrix;
	        vector<int> oneRow; 
			if(n<=0)
	        	return matrix;
	        for(int i=0;i<n;i++)
	        	oneRow.push_back(0);
	        for(int i=0;i<n;i++)
	        	matrix.push_back(oneRow);
	        
	        int rowBegin=0, rowEnd=n-1;
	        int colBegin=0, colEnd=n-1;
	        int num = 1;
	        while(rowBegin<rowEnd && colBegin<colEnd){
	        	for(int i=colBegin;i<colEnd;i++){
	        		matrix[rowBegin][i] = num++;
	        		
	        	}
	        		
	        	for(int i=rowBegin;i<rowEnd;i++)
	        		matrix[i][colEnd] = num++;
	        	for(int i=colEnd;i>colBegin;i--)
	        		matrix[rowEnd][i] = num++;
	        	for(int i=rowEnd;i>rowBegin;i--)
	        		matrix[i][colBegin] = num++;
	        	rowBegin ++; rowEnd --;
	        	colBegin ++; colEnd --;
	        }
	        if(rowBegin == rowEnd && colBegin == colEnd){
	        	matrix[rowBegin][colBegin] = num;
			}
			return matrix;	 
		}
	};
	//The code under below is used for test
	int main(){
		Solution s;
		int n=2;
		vector< vector<int> > matrix = s.generateMatrix(n);
		for(int i=0;i<n;i++){
			for(int j=0;j<n;j++)
				cout<<matrix[i][j]<<" ";
			cout<<endl;
		}
		
		system("pause");
		return 0;
	}

# Note
To solve the problem, four anchors are needed: rowBegin, rowEnd, colBegin, colEnd. The order I add number to the matrix: rowBegin, colEnd, rowEnd, colBegin. In the end, only one row or one column is remained, then add the number to it.  
