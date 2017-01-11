title: LeetCode Pascal's Triangle
date: 2015-07-08 15:45:37
tags: leetcode
---

# Description

Given numRows, generate the first numRows of Pascal's triangle.

For example, given numRows = 5,
Return

[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]


The original problem is [here](https://leetcode.com/problems/pascals-triangle/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/Pascal'sTriangle.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*Pascal's Triangle 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    vector<vector<int>> generate(int numRows) {
	        vector<vector<int>> result;
	        if(numRows <= 0)
	        	return result;
	        vector<int> oneRow;
	        oneRow.push_back(1);
	        result.push_back(oneRow);
	        if(numRows == 1)
	        	return result;
	        	
	        for(int i=1;i<numRows;i++){
	        	vector<int> row;
	        	int num = 0;
	        	row.push_back(1);
	        	for(int j=1;j<i;j++){
	        		num = result[i-1][j-1] + result[i-1][j];
	        		row.push_back(num);
	        	}
	        	row.push_back(1);
	        	result.push_back(row);
	        }
	        return result;
	    }
	};

# Note:
The number at index i of each row(except the begin and the end) is the sum of the numbers at index i-1 and i of the last row.
