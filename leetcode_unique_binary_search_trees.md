title: LeetCode Unique Binary Search Trees
date: 2015-07-11 19:20:35
tags: leetcode
---


# Description
Given n, how many structurally unique BST's (binary search trees) that store values 1...n?

For example,
Given n = 3, there are a total of 5 unique BST's.

   1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3


The original problem is [here](https://leetcode.com/problems/unique-binary-search-trees/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/UniqueBinarySearchTrees.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Unique Binary Search Trees
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	
	class Solution {
	public:
	    int numTrees(int n) {
	        vector<int> nums; 
	        nums.push_back(1);
	        for(int i=1;i<=n;i++){
	        	nums.push_back(0);
	        	if(i<=2)
	        		nums[i] = i;
	        	else{
	        		for(int j=1;j<=i;j++){
	        			nums[i] += nums[j-1]*nums[i-j];
	        		}
	        	}
	        }
	        return nums[n];
	    }
	};
	


# Note
Dynamic programming is used. For n, the number of trees is the sum of all j-1 and n-j.
