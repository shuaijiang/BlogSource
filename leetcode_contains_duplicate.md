title: LeetCode Contains Duplicate
date: 2015-06-25 19:39:07
tags: leetcode
---



# Description
Given an array of integers, find if the array contains any duplicates. Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

The original problem is [here](https://leetcode.com/problems/contains-duplicate/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ContainsDuplicate.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Contains Duplicate
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<map>
	#include<string.h>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    bool containsDuplicate(vector<int>& nums) {
	    	if(nums.size()<=1)
	    		return false;
	        map<int,int> myMap;
	        map<int,int>::iterator mapIter;
	        for(int count=0;count<nums.size();++count){
	        	if(myMap.find(nums[count])==myMap.end())
	        		myMap[nums[count]] = 1;
	        	else{
	        		myMap[nums[count]] += 1;
	        		return true;
	        	}
	        		
	        }
	        for(mapIter=myMap.begin();mapIter!=myMap.end();++mapIter){
	        	if(mapIter->second > 1)
	        		return true;
	        }
	        return false;
	    }
	};

# Note
To solve the problem, I use a hash(map in C++) to save the num and its count. If any count is bigger than 1, then return true, else return false.
