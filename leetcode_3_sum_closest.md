title: LeetCode 3 Sum Closest
date: 2015-07-25 14:26:16
tags: leetcode
---

# Description
Given an array S of n integers, find three integers in S such that the sum is closest to a given number, target. Return the sum of the three integers. You may assume that each input would have exactly one solution.

    For example, given array S = {-1 2 1 -4}, and target = 1.

    The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).

The original problem is [here](https://leetcode.com/problems/3sum-closest/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/3SumClosest.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*3Sum Closest
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<math.h>
	#include<algorithm>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
		int sumNum;
	    int threeSumClosest(vector<int>& nums, int target) {
	        int size = nums.size();
	        if(size<=2)
	        	return -1;
	        sort(nums.begin(),nums.end());
	        sumNum = nums[0] + nums[1] + nums[2];
	        for(int i=0;i<size-2;i++){
	        	if(i>0 && nums[i]==nums[i-1])
					continue;
	        	twoSum(nums, i+1, size-1, nums[i], target);
	        	if(sumNum == target)
	        		return sumNum;
	        }
	        return sumNum;
	    }
	    void twoSum(vector<int> &nums, int start, int end, int num, int target){
	    	while(start<end){
	    		int oneSum = nums[start] + nums[end] + num;
	    		if(oneSum == target){
	    			sumNum = oneSum;
	    			return;
	    		}
	    		if( oneSum < target ){
	    			if(abs(oneSum - target) < abs(sumNum - target))
						sumNum = oneSum;
	    			start ++;
	    		}
	    		else
				{
					if(abs(oneSum - target) < abs(sumNum - target))
						sumNum = oneSum;
	    			end --;
	    		}
	    	}
			return ;
	    }
	};

# Note
The problem is similar to 3sum, first sort the array. Then, for a number A in the array, select two numbers(B and C) from the set after A, which A+B+C is closest to the target. When select B and C, we find them from the head and tail of the array.
