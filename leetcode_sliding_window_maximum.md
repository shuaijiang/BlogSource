title: LeetCode Sliding Window Maximum
date: 2015-07-23 14:39:24
tags: leetcode
---

# Description
Given an array nums, there is a sliding window of size k which is moving from the very left of the array to the very right. You can only see the k numbers in the window. Each time the sliding window moves right by one position.

For example,
Given nums = [1,3,-1,-3,5,3,6,7], and k = 3.

	Window position                Max
	---------------               -----
	[1  3  -1] -3  5  3  6  7       3
	 1 [3  -1  -3] 5  3  6  7       3
	 1  3 [-1  -3  5] 3  6  7       5
	 1  3  -1 [-3  5  3] 6  7       5
	 1  3  -1  -3 [5  3  6] 7       6
	 1  3  -1  -3  5 [3  6  7]      7

Therefore, return the max sliding window as [3,3,5,5,6,7].

The original problem is [here](https://leetcode.com/problems/sliding-window-maximum/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/SlidingWindowMaximum.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Sliding Window Maximum 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<algorithm>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    vector<int> maxSlidingWindow(vector<int>& nums, int k) {
	        int size = nums.size();
	        vector<int> result;
	        int maxNum;
	        
	        if(size<=0)
	        	return result;
	        if(k==1)
	        	return nums;
	        
	        maxNum = maxArray(nums, 0, k-1);
	        result.push_back(maxNum);
	        
			for(int i=k;i<size;i++){
	        	maxNum = maxArray(nums, i-k+1, i);
	        	result.push_back(maxNum);
	        }
	        return result;
	    }
	    int maxArray(vector<int>& nums, int start, int end){
	    	int maxNum = nums[start];
			for(int i = start+1;i<=end;i++){
				if(nums[i] > maxNum)
					maxNum = nums[i];
			}
			return maxNum;
	    }
	};


# Note
To solve the problem, when sliding the window, get the maximum number.
