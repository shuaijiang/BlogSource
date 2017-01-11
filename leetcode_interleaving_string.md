title: LeetCode Interleaving String
date: 2015-09-18 16:00:56
tags: leetcode
---

# Description
Given s1, s2, s3, find whether s3 is formed by the interleaving of s1 and s2.

For example,
Given:
s1 = "aabcc",
s2 = "dbbca",

When s3 = "aadbbcbcac", return true.
When s3 = "aadbbbaccc", return false.

The original problem is [here](https://leetcode.com/problems/interleaving-string/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/InterleavingString.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Interleaving String
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<string.h>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    bool isInterleave(string s1, string s2, string s3) {
	        int m = s1.size();
	        int n = s2.size();
	        int k = s3.size();
	        if(k == 0)
	        	return true;
	        if( m+n != k)
	        	return false;
	
			vector<vector<int> >  matrix(m+1, vector<int>(n+1, 0));	
	        
			matrix[0][0] = 1;        
	        for(int i=1;i<=m;i++){
	        	if(s3[i-1] == s1[i-1])
					matrix[i][0] = 1;
				else
					break;
	        }
	        for(int j=1;j<=n;j++){
	        	if(s3[j-1] == s2[j-1])
					matrix[0][j] = 1;
				else
					break;
	        }
	        for(int i=1;i<=m;i++){
				char c1 = s1[i-1];
				for(int j=1;j<=n;j++){
					char c2 = s2[j-1];
					char c3 = s3[i+j-1];
					if(c1 == c3){
						matrix[i][j] = matrix[i-1][j] || matrix[i][j];
					}
					if(c2 == c3)
						matrix[i][j] = matrix[i][j-1] || matrix[i][j];	
				}
	        }
	        	
	        return matrix[m][n];
	    }
	};

# Note
To solve the problem, dynamic programming is used. 创建了matrix表示利用s1和s2字符串交替创建s3的路径，即 matrix[i][j]表示s1的前i个字符和s2的前j个字符创建的字符串。对于s3的当前字符c3，如果和s1的当前字符c1相等，则如果matrix[i-1][j]是真（即可以组合成s3的前i+j个字符），则matrix[i][j]也为真。 
注意

	matrix[i][j] = matrix[i-1][j] || matrix[i][j]

取或的原因是，如果c1和c3相等，但是c2和c3不相等，则matrix[i][j]会被先置为真，再置为假，如果取或，则为真。
