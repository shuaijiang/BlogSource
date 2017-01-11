title: LeetCode Single Number2
date: 2015-06-24 14:03:17
tags: leetcode
---


# Description
Given an array of integers, every element appears three times except for one. Find that single one.

Note:
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

The original problem is [here](https://leetcode.com/problems/single-number-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/SingleNumber2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Single Number
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<map>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int singleNumber(vector<int>& nums) {
	    	if(nums.size() <= 0)
	    		return 0;
	        map<int,int> nums_map;
	        map<int,int>::iterator mapIter;
	        vector<int>::iterator iter;
	        for(iter=nums.begin();iter<nums.end();++iter){
	        	int num = *iter;
	        	if(nums_map.find(num) == nums_map.end())
	        		nums_map[num] = 1;
	        	else
	        		nums_map[num] += 1;
	        }
	        for(mapIter=nums_map.begin();mapIter!=nums_map.end();++mapIter){
	        	if(mapIter->second == 1)
	        		return mapIter->first;
	        }
	        
	    }
	};


# Note
In this solution, a hash is needed(map in C++ ). We traverse the array of numbers, and put each unique number and its frequence to the hash. Then, we can get the number whos frequence is one.
