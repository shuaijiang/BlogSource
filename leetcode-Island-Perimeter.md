---
title: LeetCode Island Perimeter
date: 2017-01-11 14:02:22
tags: leetcode
---


# Description
You are given a map in form of a two-dimensional integer grid where 1 represents land and 0 represents water. Grid cells are connected horizontally/vertically (not diagonally). The grid is completely surrounded by water, and there is exactly one island (i.e., one or more connected land cells). The island doesn't have "lakes" (water inside that isn't connected to the water around the island). One cell is a square with side length 1. The grid is rectangular, width and height don't exceed 100. Determine the perimeter of the island.

Example:

[[0,1,0,0],
 [1,1,1,0],
 [0,1,0,0],
 [1,1,0,0]]

Answer: 16


The original problem is [here](https://leetcode.com/problems/island-perimeter/ "Problem").

<!--more-->

# My Solution
I solve this problem in C++, as below:
```
	class Solution {
	public:
	    int islandPerimeter(vector<vector<int>>& grid) {
	        int rowSize = grid.size();
	        if(rowSize <= 0) {
	            return 0;
	        }
	        int perimeter = 0;
	        int colSize = grid[0].size();
	        for (int i = 0; i < rowSize; i++) {
	        	for (int j = 0; j < colSize; j++) {
	        		if (grid[i][j] == 1) {
	        			perimeter += 4;
	        			if (i-1 >= 0 && grid[i-1][j] == 1)
	        				perimeter --;
	        			if (i+1 < rowSize && grid[i+1][j] == 1)
	        				perimeter --;
	        			if (j-1 >= 0 && grid[i][j-1] == 1)
	        				perimeter --;
	        			if (j+1 < colSize && grid[i][j+1] == 1)
	        				perimeter --;
	        		}
	        	}
	        }
	        return perimeter;
	    }
	};
```
# Note
To solve the problem, go throght all the island in the grid and reduce one for one neigbhood. 

