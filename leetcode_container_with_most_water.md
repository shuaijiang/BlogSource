title: LeetCode Container With Most Water
date: 2015-06-24 23:08:13
tags: leetcode
---



# Description
Given an array of integers, every element appears three times except for one. Find that single one.

Note:
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

The original problem is [here](https://leetcode.com/problems/container-with-most-water/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ContainerWithMostWater.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Container With Most Water
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
	    int maxArea(vector<int>& height) {
	        if(height.size()<=0)
	        	return 0;
			vector<int>::iterator iter1,iter2;
			int count1,count2;
			int maxNum = 0, num = 0;
			iter1=height.begin();
			count1=0;
			iter2=height.end()-1;
			count2=height.size()-1;
	        while(iter1<iter2){
	        	num = (count2 - count1) * minOfTwoNum(*iter1,*iter2) ;
	        	if(num > maxNum)
	        		maxNum = num;
	        	if(*iter1 < *iter2){
					iter1++;
					count1++;
	        	}
	        	else{
	        		iter2--;
					count2--;	
	        	}
	        }
	        return maxNum;
	    }
	    int minOfTwoNum(int x, int y){
	    	if(x<y)
	    		return x;
	    	else
	    		return y;
	    }
	};


# Note
In this solution, we use two pointers(left and right), also begin and end of the array. We move the left to right or the right to left at one step. If the number of left is smaller than the number of right, we move the left, else we move the right. Until the left is equal to right, we finish it.
