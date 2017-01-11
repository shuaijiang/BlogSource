title: LeetCode Maximum Subarray
date: 2015-07-09 20:26:22
tags: leetcode
---

# Description
Find the contiguous subarray within an array (containing at least one number) which has the largest sum.

For example, given the array [−2,1,−3,4,−1,2,1,−5,4],
the contiguous subarray [4,−1,2,1] has the largest sum = 6.

The original problem is [here](https://leetcode.com/problems/maximum-subarray/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/MaximumSubarray.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*Maximum Subarray 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<map>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int maxSubArray(vector<int>& nums) {
	        if(nums.size()<=0)
	        	return 0;
			int maxSum=nums[0], sum=nums[0];
	        for(int i=1;i<nums.size();i++){
	        	if(sum < 0)
	        		sum = 0;
	        	sum += nums[i];
	        	maxSum = max(maxSum, sum);
	        }
	        return maxSum; 
	    }
	};


# Note
To solve the problem, Jay Kadane's algorithm is used. During traversal the array, we get the sum of the elements, if sum is less than zero, we set it to zero, and go on computing the sum. When a new element come, we also judge whether the sum is the maximum by now. Finally, we get the maximum of the sum. 
