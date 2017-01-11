title: LeetCode Valid Sudoku
date: 2015-06-28 16:13:03
tags: leetcode
---

# Description

Determine if a Sudoku is valid, according to: [Sudoku Puzzles - The Rules](http://sudoku.com.au/TheRules.aspx).

The Sudoku board could be partially filled, where empty cells are filled with the character '.'.

![sudoku](/image/sudoku.png)

A partially filled sudoku which is valid.

The original problem is [here](https://leetcode.com/problems/valid-sudoku/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ValidSudoku.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Valid Sudoku
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    bool isValidSudoku(vector<vector<char>>& board) {
	        for(int row=0;row<board.size();row++){
	        	if(!isValid(board,row,row,0,board[row].size()-1))
	        		return false;
	        }
	        for(int col=0;col<board[0].size();col++){
	        	if(!isValid(board,0,board.size()-1,col,col))
	        		return false;
	        }
	        for(int row=0;row<board.size();row+=3){
	        	for(int col=0;col<board[0].size();col+=3){
	        		if(!isValid(board,row,row+2,col,col+2))
	        			return false;
	        	}
	        }
	        return true;
	    }
	    bool isValid(vector<vector<char>>& board, int rowi, int rowj, int coli, int colj) {
	    	int index[10]={0};
	    	int num;
	    	for(int row=rowi;row<=rowj;row++){
	    		for(int col=coli;col<=colj;col++){
	    			if(board[row][col]!='.'){
	    				num = board[row][col] - '0';
	    				index[num] += 1;
	    				if(index[num] > 1)
	    					return false;
	    			}
	    		}
	    	}
	    	return true;
	    }
	};

# Note
To solve the problem, just check whether each row(each column, each 3*3 area) has repeat digitals resoectively. 
