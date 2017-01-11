title: LeetCode Search For A Range
date: 2015-07-21 22:51:29
tags: leetcode
---

# Description
Given a sorted array of integers, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return [-1, -1].

For example,
Given [5, 7, 7, 8, 8, 10] and target value 8,
return [3, 4].

The original problem is [here](https://leetcode.com/problems/search-for-a-range/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/SearchForARange.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Search for a Range
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    vector<int> searchRange(vector<int>& nums, int target) {
	        vector<int> notfound, result;
	        notfound.push_back(-1);
	        notfound.push_back(-1);
	        result.push_back(0);
	        result.push_back(0);
	        
	        int size = nums.size();
	        if(size <= 0)
	        	return notfound;
	        if(size == 1 && nums[0] == target)
	        	return result;
	        
			int begin=0, end= size-1, middle=0;
			bool isfind = false;
			int index = 0;
			while(begin <= end){
				if(begin == end){
					if(nums[begin] != target)
						return notfound;
					else{
						isfind = true;
						index = begin;
					}	
					break;
				}
				middle = (begin + end) / 2;
				if(nums[middle] == target){
					isfind = true;
					index = middle;
					break;
				}
				else if(nums[middle] < target)
					begin = middle + 1;
				else
					end = middle - 1;
			}
			if(isfind){
				int i = index-1;
				
				while(i>=0 && nums[i]==target)
					i--;
				
				begin = i+1;
				i = index + 1;
				while(i<size && nums[i]==target)
					i++;
				end = i - 1;
				
				result[0] = begin;
				result[1] = end;
				return result;
			}
			else
				return notfound; 
	    }
	};
	// the code under below is used for test
	int main(){
		Solution s;
		vector<int> nums;
		nums.push_back(1);
		nums.push_back(3);
		
		vector<int> result = s.searchRange(nums, 1);
		for(int i=0;i<result.size();i++)
			cout<<result[i]<<endl;
			
		system("pause");
		return 0;
	}


# Note
To solve the problem, my algorithm's runtime complexity must be in the order of O(log n). So, binary search is used. If we get the index of the target, we just need find the begin and tail of the range.
