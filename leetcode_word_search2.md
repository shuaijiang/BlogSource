title: LeetCode Word Search 2
date: 2015-10-21 10:23:59
tags: leetcode
---

# Description
Given a 2D board and a list of words from the dictionary, find all words in the board.

Each word must be constructed from letters of sequentially adjacent cell, where "adjacent" cells are those horizontally or vertically neighboring. The same letter cell may not be used more than once in a word.

For example,
Given words = ["oath","pea","eat","rain"] and board =
	
	[
	  ['o','a','a','n'],
	  ['e','t','a','e'],
	  ['i','h','k','r'],
	  ['i','f','l','v']
	]
Return ["eat","oath"].

The original problem is [here](https://leetcode.com/problems/word-search-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/WordSearch2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Word Search II 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	using namespace std;
	
	
	class TrieNode{
	public:	
		bool iskey;
		TrieNode * childern[26];
		TrieNode(){
			iskey = false;
			for(int i=0;i<26;++i){
				childern[i] = NULL;
			}
		}
	};
	class Solution {
	public:
		vector<string> res;
		int row;
		int col;
	    vector<string> findWords(vector<vector<char>>& board, vector<string>& words) {
	        root = new TrieNode();
	        
	        int wordNum = words.size();
	        if(wordNum <= 0)
	        	return res;
	        
			row = board.size();        
	        col = board[0].size();
	        
	        //create tried tree 
	        for(int i=0;i<wordNum;++i){
	        	string word = words[i];
	        	int wordLen = word.size();
	        	TrieNode * node = root;
	        	char ch;
	        	for(int j=0;j<wordLen;++j){
	        		ch = word[j];
	
					if(node->childern[ch - 'a'] == NULL){
	        			node->childern[ch - 'a'] = new TrieNode() ;
	        		}
	        		if(j == wordLen-1){
	        			node->childern[ch - 'a']->iskey = true;
	        		}
	        		node =  node->childern[ch-'a'];
	        		
	        	}
	        }
	        // find the words in the board
	        
	        for(int i=0;i<row;i++){
	        	for(int j=0;j<col;j++){
	        		vector<vector<bool>> path(row, vector<bool>(col, false));
					char ch = board[i][j];
					if(root->childern[ch-'a'] != NULL)
						find(board, path, i, j, root, "");
	        	}
	        }
	        return res;
	    }
	    void find(vector<vector<char>>& board, vector<vector<bool>> &path, int i, int j, TrieNode *node, string str){
	    	if(i<0 || i>=row || j< 0 || j>=col)
	    		return;
	    	if(path[i][j])
	    		return ;
	    	char ch = board[i][j];
	    	node = node->childern[ch-'a'];
	    	if(node == NULL)
	    		return;
	
	    	str.push_back(ch);
	    	if(node->iskey){
	    		res.push_back(str);
	    		node->iskey = false;
	    	}
	    	
	    	path[i][j] = true;
	    	if(i-1>=0 && i-1<row)
	    		find(board, path, i-1, j, node, str);
	    	if(i+1>=0 && i+1<row)
				find(board, path, i+1, j, node, str);
	    	if(j-1>=0 && j-1<col)
			find(board, path, i, j-1, node, str);
	    	if(j+1>=0 && j+1<col)
				find(board, path, i, j+1, node, str);
				
			path[i][j] = false;	//should be set to false
	    }
	private:
		TrieNode * root;
	};
	
	int main(){
		Solution s;
		vector<vector<char>> board(1,vector<char>(2,'a'));
		vector<string> words(1,"a");
		vector<string> res = s.findWords(board, words);
		cout<<"res.size"<<res.size();
		/*
		for(int i=0;i<res.size();++i){
			cout<<res[i]<<endl;
		}*/
		return 0;
	
	}

# Note
采用前缀树保存字典中所有单词。在搜索词的过程中，使用了深度优先遍历（DFS）。需要注意的是，利用一个和board相同大小的2维矩阵保存是否访问过某个字母，访问时设置对应位置为true，访问后设置其为false, 否则会得到错误结果。
