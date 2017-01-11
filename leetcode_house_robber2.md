title: LeetCode House Robber2
date: 2015-09-17 18:04:21
tags: leetcode
---


# Description
Note: This is an extension of House Robber.

After robbing those houses on that street, the thief has found himself a new place for his thievery so that he will not get too much attention. This time, all houses at this place are arranged in a circle. That means the first house is the neighbor of the last one. Meanwhile, the security system for these houses remain the same as for those in the previous street.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

The original problem is [here](https://leetcode.com/problems/house-robber-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/HouseRobber2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*House Robber
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int rob(vector<int>& nums) {
	    	int size = nums.size();
	    	if(size <= 0)
	    		return 0;
	    	if(size == 1)
	    		return nums[0];    	
	    	if(size == 2)
	    		return max(nums[0], nums[1]);
	    	
	    	vector<int> money = vector<int>(size, 0);
	    	vector<int> index = vector<int>(size, 0);
	    	//Dynamic programming
	    	money[0] = nums[0];
	    	index[0] = 1;
	    	money[1] = max(nums[0],nums[1]);
	    	if(nums[0] > nums[1])
	    		index[1] = 1;
	    	else
	    		index[1] = 0;
	    	for(int count=2;count<size;++count){
	    		money[count] = max(money[count-1],money[count-2]+nums[count]);    		
	    		if( money[count-1] >= money[count-2]+nums[count] ){
					if(count == size-1)
						return money[count];
					index[count] = index[count-1];
				} 
	    		else
	    			index[count] = index[count-2];
	    	}
	    	if(index[size-1] == 0)
	    		return money[size-1];
	    	//The result without the last one 
			int max1 = money[size-2];
	    	
	    	money[1] = nums[1];
	    	money[2] = max(nums[1],nums[2]);
	    	//Compute the result without the first one
			for(int count=3;count<size;++count){
	    		money[count] = max(money[count-1],money[count-2]+nums[count]);    		
	    	}
	    	//return the max of the two results
	    	return max(money[size-1], max1);
	    }
	};

# Note
To solve the problem, dynamic programming is used. Assume the robber get one house i, he just need to compute the maximum of the  nums[i-1] and (nums[i-2]+nums[i]) as the money[i], this will not alert police. In the end, the robber can get the maximum of money[end-1]; Additionally, the first and the end of the house can't be robbed at the same time.
