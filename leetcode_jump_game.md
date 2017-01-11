title: LeetCode Jump Game
date: 2015-08-02 16:29:23
tags: leetcode
---


# Description
Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

For example:
A = [2,3,1,1,4], return true.

A = [3,2,1,0,4], return false.

The original problem is [here](https://leetcode.com/problems/jump-game/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/JumpGame.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Jump Game 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    bool canJump(vector<int>& nums) {
	        int size = nums.size();
	        if(size <= 1)
	        	return true;
	        vector<bool> path(size,false);
	        path[0] = true;
	        int currIndex = 0;
	        int nextIndex = nums[0];
	        while(currIndex <= nextIndex && currIndex < size){
	        	int temp = nextIndex;
				for(int j=currIndex;j<=nextIndex && j<size;j++){
					path[j] = true;
					if(nums[j] + j > nextIndex){			
						nextIndex = nums[j] + j;
					}		
				}
				currIndex = temp + 1;
	        }
	        return path[size-1];
	    }
	};


# Note
To solve the problem, greedy algorithm is used. We need currIndex and nextIndex to label the positions of one step. The path between the currIndex and nextIndex can be reached, and we can get the next nextIndex if nums[currIndex] + currIndex are larger than the nextIndex.  Steps by steps, finally we kown whether we reach the last one.
