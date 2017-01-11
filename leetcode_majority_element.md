title: LeetCode Majority Element
date: 2015-06-25 11:33:10
tags: leetcode
---


# Description
Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

You may assume that the array is non-empty and the majority element always exist in the array.

The original problem is [here](https://leetcode.com/problems/majority-element/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/MajorityElement.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Majority Element 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<math.h>
	#include<vector>
	#include<map>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int majorityElement(vector<int>& nums) {
	    	if(nums.size() == 0)
	    		return 0;
	        map<int,int> myMap;
	        map<int,int>::iterator mapIter;
	        
	        vector<int>::iterator iter;
	        int n = 0;
	        for(iter=nums.begin();iter<nums.end();++iter){
	        	if(myMap.find(*iter) == myMap.end())
	        		myMap[*iter] = 1;
	        	else
	        		myMap[*iter] += 1;    		
	        }
	        n = nums.size()/2;
	        int max = 0, maxCount = 0;
	        mapIter=myMap.begin();
	        max = mapIter->first;
	        maxCount = mapIter->second; 
	        for(mapIter=myMap.begin();mapIter!=myMap.end();++mapIter) {
	        	if(mapIter->second >= maxCount){
	        		max = mapIter->first;
	        		maxCount = mapIter->second;
	        	}
	        }
	        return max;
	    }
	};


# Note
To solve the problem, I use a hash(map in C++) to save the num and its count. Then, the num with maximum count is the result.
