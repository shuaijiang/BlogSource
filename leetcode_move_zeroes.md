title: LeetCode Move Zeros
date: 2015-09-24 11:09:47
tags: leetcode
---


# Description
Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].

Note:
	You must do this in-place without making a copy of the array.
	Minimize the total number of operations.


The original problem is [here](https://leetcode.com/problems/move-zeroes/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/MoveZeroes.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Move Zeroes
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    void moveZeroes(vector<int>& nums) {
	        int size = nums.size();
	        int end=size-1;
	
			for(int i=0;i<end;i++){
				if(nums[i] != 0){
					continue;
				}
				else{
					for(int j=i;j<end;j++){
						nums[j]=nums[j+1];
					}
					nums[end]=0;
					end --;
					i--; //the numbers after zero move one step to the front, so the index i need one step move
				}
			}
	    }
	};
	
	int main() {
		Solution s;
		vector<int> nums;
		nums.push_back(0);
		nums.push_back(0);
		nums.push_back(1);
		//nums.push_back(3);
		
		s.moveZeroes(nums);
		for(int i=0;i<nums.size();i++){
			cout<<nums[i]<<endl;
		}
		system("pause");
		return 0;
	}

# Note
遍历数组，寻找0，通过冒泡方法，将0放置到数组的尾部.需要标记尾部已经确定的0的起始位置(end)；如果找到一个0，还需要把遍历的标记向前数组的起始方向移动一步（i--），因为非0的数向数组起始方向前移了一步。
