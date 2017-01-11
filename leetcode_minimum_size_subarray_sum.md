title: LeetCode Minimum Size Subarray Sum
date: 2015-07-23 11:44:34
tags: leetcode
---

# Description
Given an array of n positive integers and a positive integer s, find the minimal length of a subarray of which the sum ≥ s. If there isn't one, return 0 instead.

For example, given the array [2,3,1,2,4,3] and s = 7,
the subarray [4,3] has the minimal length under the problem constraint.


The original problem is [here](https://leetcode.com/problems/minimum-size-subarray-sum/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/MinimumSizeSubarraySum.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Minimum Size Subarray Sum 
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
	    int minSubArrayLen(int s, vector<int>& nums) {
	    	int size = nums.size();
	    	int begin=0;
	    	if(size<=0)
	    		return 0;
	    	int len = 1, minLen = size, totalNum = nums[0];
	    	int i = 1;
	    	while(totalNum < s && i < size){
				totalNum += nums[i];
				i ++;
				len ++;
			}
			if(totalNum < s)
				return 0;
			i--;
			do{
				while(totalNum > s){
					totalNum -= nums[begin];
					len --;
					begin ++;
				}
				if(totalNum < s && begin >= 1){
					begin --;
					totalNum += nums[begin];
					len ++;
				}
				if(len < minLen)
					minLen = len;
					
	    		i++;
	    		if(i<size){
	    			totalNum += nums[i];
	    			len ++;
	    		}    		
	    	}while(i<size);
	    	
	    	if(totalNum < s)
	    		return 0;
	    	else
	    		return minLen;
	    }
	};
	// the code under below is used for test
	int main(){
		Solution s;
		vector<int> nums;
		nums.push_back(1);
		nums.push_back(4);
		nums.push_back(4);
		
		int result = s.minSubArrayLen(4,nums);
		cout<<"result="<<result<<endl;
		system("pause");
		return 0;
	}

# Note
To solve the problem, two position indces are needed. Traversal the array from begin to end, after adding each number, we drop some elements from the begining of the subarray, in the same time the sum of the subarray is equal to or larger than the target. Then, we can get the minimum size of the subarray. 
