title: LeetCode Kth Largest Element in an Array 
date: 2015-06-25 23:23:27
tags: leetcode
---




# Description
Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.

For example,
Given [3,2,1,5,6,4] and k = 2, return 5.

Note: 
You may assume k is always valid, 1 ≤ k ≤ array's length.

The original problem is [here](https://leetcode.com/problems/kth-largest-element-in-an-array/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/KthLargestElementInAnArray.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Kth Largest Element in an Array 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	
	#include<iostream>
	#include<vector>
	#include<map>
	#include<string.h>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int findKthLargest(vector<int>& nums, int k) {
	        int *KNum = new int[k];
	        int minNum,minIndex;
	        for(int i=0;i<k;i++){
	        	KNum[i] = nums[i];
	        }
	        minIndex = minIndexOfNums(KNum,k);
	        minNum   = KNum[minIndex];
	        for(int i=k;i<nums.size();i++){
	        	if(nums[i]>minNum){
	        		KNum[minIndex] = nums[i];
	        		minIndex = minIndexOfNums(KNum,k);
	        		minNum   = KNum[minIndex];
	        	}
	        }
	        return minNum;
	    }
	    int minIndexOfNums(int *num, int k){
	    	int min = num[0];
	    	int index = 0;
	    	for(int count=1;count<k;count++){
	    		if(num[count]<min){
	    			min = num[count];
	    			index = count;
	    		}
	    	}
	    	return index;
	    }
	};

# Note
To solve the problem, I create a array KNum to save the top k largest numbers. if any number in the input array nums is larger than the minimum in the KNum, then replace the number with the minimum. Repeate these steps, untils the end of the array. Finally, the minimum number of the KNum is what we wanted.
