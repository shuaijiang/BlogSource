title: LeetCode Surrounded Regions
date: 2015-08-12 13:15:23
tags: leetcode
---

# Description
Given a 2D board containing 'X' and 'O', capture all regions surrounded by 'X'.

A region is captured by flipping all 'O's into 'X's in that surrounded region.

For example,

	X X X X
	X O O X
	X X O X
	X O X X
After running your function, the board should be:

	X X X X
	X X X X
	X X X X
	X O X X

The original problem is [here](https://leetcode.com/problems/surrounded-regions/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/SurroundedRegions.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Surrounded Regions 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:	
	    void solve(vector<vector<char>>& board) {
	    	int rowNum = board.size();
	    	if(rowNum <= 2)
	    		return;
	    	int colNum = board[0].size();
	    	if(colNum <= 2)
	    		return;
	    	
	        for(int j=0; j < colNum; j++){
	        	if(board[0][j] == 'O')
					isRegion(board, 0, j, rowNum, colNum);
				if(board[rowNum-1][j] == 'O') 
					isRegion(board, rowNum-1, j, rowNum, colNum);
			}
			for(int i=0; i < rowNum; i++){
				if(board[i][0] == 'O') 
					isRegion(board, i, 0, rowNum, colNum);
				if(board[i][colNum-1] == 'O')
					isRegion(board, i, colNum-1, rowNum, colNum);
			}
	        
	        for(int i = 0; i < rowNum; i++){
	        	for(int j = 0; j < colNum; j++){
					if(board[i][j] == 'O')
						board[i][j] = 'X';
					else if(board[i][j] == '_') 
						board[i][j] = 'O';
	        	}
	        }
	        return;
	    }
	    void isRegion(vector<vector<char>>& board, int i, int j, int row, int col){
	    	if(board[i][j] == 'O')
	    		board[i][j] = '_';
	    	else
	    		return;
			if(i > 1 && board[i-1][j] == 'O')
	        {
	            //board[i-1][j] = '_';
	            isRegion(board, i-1, j, row, col);
	        }
	        if(i < row-1 && board[i+1][j] == 'O')
	        {
	            //board[i+1][j] = '_';
	            isRegion(board, i+1, j, row, col);
	        }
	        if(j > 1 && board[i][j-1] == 'O')
	        {
	           // board[i][j-1] = '_';
	            isRegion(board, i, j-1, row, col);
	        }
	        if(j < col-1 && board[i][j+1] == 'O')
	        {
	            //board[i][j+1] = '_';
	            isRegion(board, i, j+1, row, col);
	        }
	    	return;
	    }
	};


# Note
The problem is similar to the problem[Number of Islands](https://leetcode.com/problems/number-of-islands/). We just traversal the number at the first row, first column, last row and last column. Then depth-first search from the number to find the 'O'. The 'O's which are not visited need converted to 'X'.  
