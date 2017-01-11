title: LeetCode Word Search
date: 2015-08-12 23:14:06
tags: leetcode
---

# Description
Given a 2D board and a word, find if the word exists in the grid.

The word can be constructed from letters of sequentially adjacent cell, where "adjacent" cells are those horizontally or vertically neighboring. The same letter cell may not be used more than once.

For example,
Given board =

	[
	  ["ABCE"],
	  ["SFCS"],
	  ["ADEE"]
	]
word = "ABCCED", -> returns true,
word = "SEE", -> returns true,
word = "ABCB", -> returns false.

The original problem is [here](https://leetcode.com/problems/word-search/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/WordSearch.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*
	*Word Search
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    bool exist(vector<vector<char>>& board, string word) {
	        int rowNum = board.size();
	        if(rowNum <= 0)
	        	return false;
	        int colNum = board[0].size();
	        vector<vector<char>> myBoard = board;
			for(int i=0;i<rowNum;i++){
				for(int j=0;j<colNum;j++){
					if(board[i][j] == word[0]){
						myBoard = board;
						if(same(myBoard,i,j,word,0))
							return true;
					}
				}
			}
			return false;
	    }
	    bool same(vector<vector<char>> &board, int i, int j, string word, int index){
	    	if(index == word.size()-1){
				if(board[i][j] == word[index])
					return true;
				else
					return false;
			} 
			else{
				if(board[i][j] == word[index])
					board[i][j] = '_';
				else
					return false;
				bool flag = false;
				if(i>0){
					vector<vector<char>> myBoard = board;
					flag = flag || same(myBoard, i-1, j, word, index+1);
				}
					
				if(i<board.size()-1){
					vector<vector<char>> myBoard = board;
					flag = flag || same(myBoard, i+1, j, word, index+1);
				}
					
				if(j>0){
					vector<vector<char>> myBoard = board;
					flag = flag || same(myBoard, i, j-1, word, index+1);
				}
					
				if(j<board[0].size()-1){
					vector<vector<char>> myBoard = board;
					flag = flag || same(myBoard, i, j+1, word, index+1);
				}
					
				return flag;
			}
	    }
	};

# Note
I use depth-first search to find the word in the borad. The same letter cell may not be used more than once, so the used letter was labeled.
