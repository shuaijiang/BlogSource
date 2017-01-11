title: LeetCode House Robber
date: 2015-06-25 14:19:43
tags: leetcode
---



# Description
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.
The original problem is [here](https://leetcode.com/problems/house-robber/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/HouseRobber.cpp "Code").
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
	#include<map>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int rob(vector<int>& nums) {
	    	vector<int>::iterator iter=nums.begin();
	    	if(nums.size() <= 0)
	    		return 0;
	    	if(nums.size() == 1)
	    		return *iter;
	    	
	    	int size = nums.size();
	    	int *money = new int[size];
	    	//Dynamic programming
	    	money[0] = nums[0];
	    	money[1] = max(nums[0],nums[1]);
	    	for(int count=2;count<size;++count){
	    		money[count] = max(money[count-1],money[count-2]+nums[count]);
	    	}
	    	return money[size-1];
	    }
	};
	//The code under below is used for test
	int main()
	{
		Solution s;
		vector<int> nums;
		nums.push_back(1);
		nums.push_back(12);
		nums.push_back(3);
		
		int maxMoney = s.rob(nums);
		cout<<"money="<<maxMoney<<endl;
		system("pause");
		return 0;
	}


# Note
To solve the problem, dynamic programming is used. Assume the robber get one house i, he just need to compute the maximum of the  nums[i-1] and (nums[i-2]+nums[i]) as the money[i], this will not alert police. In the end, the robber can get the maximum of money[end-1]; 
