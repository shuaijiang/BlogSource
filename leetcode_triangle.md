title: LeetCode Triangle
date: 2015-07-21 13:51:59
tags: leetcode
---

# Description
Given a triangle, find the minimum path sum from top to bottom. Each step you may move to adjacent numbers on the row below.

For example, given the following triangle

	[
	     [2],
	    [3,4],
	   [6,5,7],
	  [4,1,8,3]
	]
The minimum path sum from top to bottom is 11 (i.e., 2 + 3 + 5 + 1 = 11).

The original problem is [here](https://leetcode.com/problems/triangle/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/Triangle.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Triangle 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int minimumTotal(vector<vector<int> >& triangle) {
	        vector<vector<int> > distance = triangle;
	        int rowSize = distance.size();
	        if(rowSize<=0)
	        	return 0;
	        if(rowSize == 1)
	        	return distance[0][0];
	        
	        for(int i=1;i<rowSize;i++){
	        	int colSize = i+1;
	        	for(int j=0;j<colSize;j++){
	        		if(j==0)
	        			distance[i][j] += distance[i-1][0];
					else if(j==colSize-1) 
	        			distance[i][j] += distance[i-1][j-1];
	        		else
	        			distance[i][j] += min(distance[i-1][j-1],distance[i-1][j]);
				}
	        }
	        int minTotal = distance[rowSize-1][0];
	        int colSize = distance[rowSize-1].size();
			for(int i=1;i<colSize;i++){
	        	if(distance[rowSize-1][i] < minTotal)
	        		minTotal = distance[rowSize-1][i];
	        }
	        return minTotal;
	    }
	};
	
	int main(){
		Solution s;
		vector<vector<int> > triangle;
		vector<int> oneRow;
		oneRow.push_back(-1);
		triangle.push_back(oneRow);
		oneRow.clear();
		oneRow.push_back(-2);
		oneRow.push_back(-3);
		triangle.push_back(oneRow);
		int total = s.minimumTotal(triangle);
		cout<<"total="<<total<<endl;
		
		system("pause");
		return 0;
	}


# Note
To solve the problem, a vector distance which has the same size with the vector triangle is used to save the minimum path sum from the begin to the current. Finally, we just compute the minimum path sum of the last row in the vector.  
