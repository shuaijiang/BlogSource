title: LeetCode Contains Duplicate2
date: 2015-06-25 20:06:35
tags: leetcode
---




# Description
Given an array of integers and an integer k, find out whether there there are two distinct indices i and j in the array such that nums[i] = nums[j] and the difference between i and j is at most k.

The original problem is [here](https://leetcode.com/problems/contains-duplicate-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ContainsDuplicate2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Contains Duplicate2
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
	    bool containsNearbyDuplicate(vector<int>& nums, int k) {
	    	if(nums.size()<=1)
	    		return false;
	        map<int,int> myMap;
	        map<int,int>::iterator mapIter;
	        for(int count=0;count<nums.size();++count){
	        	if(myMap.find(nums[count])==myMap.end())
	        		myMap[nums[count]] = count;
	        	else{
	        		if(count - myMap[nums[count]] <= k)
	        			return true;
	        		else
	        			myMap[nums[count]] = count;
	        	}
	        		
	        }
	        return false;
	    }
	};

# Note
To solve the problem, I use a hash(map in C++) to save the num and its index. If a new num is in the map, compute the difference of the index. If the difference is not larger than k, then return true. Finally, if not return true before, then return false.
