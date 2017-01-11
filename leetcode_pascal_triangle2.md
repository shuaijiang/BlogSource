title: LeetCode Pascal's Triangle2
date: 2015-07-09 23:00:57
tags: leetcode
---

# Description
Given an index k, return the kth row of the Pascal's triangle.

For example, given k = 3,
Return [1,3,3,1].

The original problem is [here](https://leetcode.com/problems/pascals-triangle-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/Pascal'sTriangle2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*Pascal's Triangle II 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    vector<int> getRow(int rowIndex) {
	        vector<int> lastRow;
			vector<int> row;
	        if(rowIndex < 0)
	        	return row;
	
	        lastRow.push_back(1);
	
	        if(rowIndex == 0)
	        	return lastRow;
	        	
	        for(int i=1;i<=rowIndex;i++){
	        	int num = 0;
	        	row.push_back(1);
	        	for(int j=1;j<i;j++){
	        		num = lastRow[j-1] + lastRow[j];
	        		row.push_back(num);
	        	}
	        	row.push_back(1);
	        	lastRow = row;
	        	row.clear();
	        }
	        return lastRow;
	    }
	};


# Note
The number at index i of each row(except the begin and the end) is the sum of the numbers at index i-1 and i of the last row. 
