title: LeetCode Median of Two Sorted Arrays
date: 2015-07-22 09:58:49
tags: leetcode
---

# Description
There are two sorted arrays nums1 and nums2 of size m and n respectively. Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

The original problem is [here](https://leetcode.com/problems/median-of-two-sorted-arrays/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/MedianOfTwoSortedArrays.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Median of Two Sorted Arrays
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<math.h>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
	        vector<int> nums;
	        double result = 0;
	        int size1 = nums1.size(), size2 = nums2.size();
	        if(size1+size2 <= 0)
	        	return result;
	        int i=0, j=0;
	        while(i<size1 && j<size2){
	        	if(nums1[i] <= nums2[j]){
	        		nums.push_back(nums1[i]);
	        		i++;
	        	}
	        	else{
	        		nums.push_back(nums2[j]);
	        		j++;
	        	}
	        }
	        while(i<size1){
	        	nums.push_back(nums1[i]);
	        	i++;
	        }
	        while(j<size2){
	        	nums.push_back(nums2[j]);
	        	j++;
	        }
	        if((size1+size2)%2 == 0){
	        	int middle = (size1+size2)/2;
		        result = (nums[middle]+nums[middle-1])/2.0;
	        }
			else{
				int middle = (size1+size2)/2;
		        result = nums[middle];	   
			}
			return result;
	
	    }
	};


# Note
To solve the problem, I first merge the two arrays. Then find the median of the sorted array. 
