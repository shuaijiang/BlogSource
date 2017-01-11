title: LeetCode Number Of Islands
date: 2015-06-26 22:17:34
tags: leetcode
---



# Description
Given a 2d grid map of '1's (land) and '0's (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

Example 1:

11110

11010

11000

00000

Answer: 1

Example 2:

11000

11000

00100

00011

Answer: 3


The original problem is [here](https://leetcode.com/problems/number-of-islands/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/NumberOfIslands.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*
	*Number of Islands
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int numIslands(vector<vector<char>>& grid) {
	    	int num = 0;
	        for(int i=0;i<grid.size();++i){
	        	for(int j=0;j<grid[i].size();++j){
	        		if(isIsland(grid,i,j)){
	        			num ++;
	        		}
	        	}
	        }
	        return num;
	    }
	    bool isIsland(vector<vector<char>>& grid, int i, int j){
	    	if(i>=0 && i<grid.size() && j >=0 && j<=grid[i].size() && grid[i][j]=='1'){
	    		grid[i][j]='_';
	    		isIsland(grid,i-1,j);
	    		isIsland(grid,i+1,j);
	    		isIsland(grid,i,j-1);
	    		isIsland(grid,i,j+1);
	    		return true;
	    	}
	    	return false;
	    }
	};



# Note
In the solution, recursion is needed. 
