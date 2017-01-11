title: LeetCode Rotate Image
date: 2015-07-12 15:29:33
tags: leetcode
---


# Description
You are given an n x n 2D matrix representing an image.

Rotate the image by 90 degrees (clockwise).

Follow up:
Could you do this in-place?

The original problem is [here](https://leetcode.com/problems/rotate-image/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/RotateImage.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Rotate Image
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    void rotate(vector<vector<int>>& matrix) {
	        int size = matrix.size();
			for(int i=0;i<size/2;i++){
				
				for(int j=i;j<size-i-1;j++){
					int num = matrix[i][j];
					matrix[i][j] = matrix[size-j-1][i];
					matrix[size-j-1][i] = matrix[size-i-1][size-j-1];
					matrix[size-i-1][size-j-1] = matrix[j][size-i-1];
					matrix[j][size-i-1] = num;
				}
			}
			return;
	    }
	};


# Note
To rotate the image, I rotate the "circle" from outside to the center. For example, the first row, last row, first column and last column together to make up one circle. 
