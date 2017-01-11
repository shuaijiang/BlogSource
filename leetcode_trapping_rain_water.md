title: LeetCode Trapping Rain Water
date: 2015-07-21 12:52:04
tags: leetcode
---


# Description
Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it is able to trap after raining.

For example, 
Given [0,1,0,2,1,0,1,3,2,1,2,1], return 6.

The original problem is [here](https://leetcode.com/problems/trapping-rain-water/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/TrappingRainWater.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Trapping Rain Water 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int trap(vector<int>& height) {
	        int size = height.size();
	        if(size<=1) 
	        	return 0;
	        int left=0, right=size-1;
	        int area = 0, secondH = 0;
	        while(left < right){
	        	if(height[left] < height[right]){
	        		secondH = max(height[left], secondH);
	        		area += secondH - height[left];
	        		left ++;
	        	}
	        	else{
	        		secondH = max(height[right],secondH);
	        		area += secondH - height[right];
	        		right --;
	        	}
	        }
	        return area;
	    }
	};

# Note
To solve the problem, reference to  [here](http://www.xuebuyuan.com/1586534.html "Reference").  We traversal the vector from head and tail to the middle. If the left height is less than the right one, we move the left one to right by one step, else we move the right one to left by one step. And each step, we compute the secondHeight and the added area by secondHeight - left height or right height.  
