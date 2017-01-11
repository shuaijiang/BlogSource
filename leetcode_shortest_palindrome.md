title: LeetCode Shortest Palindrome
date: 2015-09-18 10:51:17
tags: leetcode
---

# Description
Given a string S, you are allowed to convert it to a palindrome by adding characters in front of it. Find and return the shortest palindrome you can find by performing this transformation.

For example:

Given "aacecaaa", return "aaacecaaa".

Given "abcd", return "dcbabcd".

The original problem is [here](https://leetcode.com/problems/shortest-palindrome/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ShortestPalindrome.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Shortest Palindrome
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
		//Manacher algorithm
		int longestPalindrom(string s) {
	        int len = s.size();
			string s1;
	        s1.resize(2 * s.length() + 2);
	        int idx = 0;
	        s1[idx++] = '$';
	        s1[idx++] = '#';
	        for (int i=0;i<s.size(); i++) {
	            s1[idx++] = s[i];
	            s1[idx++] = '#';
	        }
	        vector<int> p(s1.length(), 0);
	        int res = 0;
	        for (int id = 0, i = 1; i < s1.length(); ++i) {
	            if (i < id + p[id]) 	// mx = id + p[id]
					p[i] = min(p[2 * id - i], id + p[id] - i);
	            else 
					p[i] = 1;
	            //compute the p
	            while (s1[i + p[i]] == s1[i - p[i]]) 
					++p[i];
				
	            if (id + p[id] < i + p[i]) 
					id = i;
	            //the palindrome start from the beginning
				if (p[i] == i)
					res = max(res, i);
	        }
	        return res - 1;
	    }
	    string shortestPalindrome(string s) {
	        int len = s.size();
			if(len <= 1)
				return s;
			int index = longestPalindrom(s) - 1;
			cout<<"index="<<index<<endl;
			string res;
			for(int i=len-1;i>index;i--)
				res.push_back(s[i]);
			res = res + s;
			
			return res;
	    }
	};

# Note
解题思路：首先，寻找以字符串第一个字符为起点的最长回文串；再将字符串中后面不属于回文的部分倒置，并防止新字符串的开始，然后再把该回文串放在其之后。

在寻找回文串的过程中，如果只是通过遍历，会超时。所以，采用Manacher算法，时间复杂度为O(n)。参考博客![here](http://www.cnblogs.com/easonliu/p/4522724.html)
