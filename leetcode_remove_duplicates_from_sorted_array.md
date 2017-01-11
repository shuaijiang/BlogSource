title: LeetCode Remove Duplicates from Sorted Array
date: 2015-06-19 09:37:25
tags: leetcode
---

# Description
Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this in place with constant memory.

For example,
Given input array nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively. It doesn't matter what you leave beyond the new length.

The original problem is [here](https://leetcode.com/problems/remove-duplicates-from-sorted-array/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/RemoveDuplicatesFromSortedArray.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Remove Duplicates from Sorted Array 
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
	    int removeDuplicates(vector<int>& nums) {
	    	if(nums.size()==0)
	    		return 0;
	        vector<int> nums1;
	        vector<int>::iterator iter,iter1;
	        int last_num;
	        int total_num = 0;
			for(iter=nums.begin();iter<nums.end();++iter) {
				nums1.push_back(*iter);
			}
			iter = nums.begin();
			last_num = *iter;
			iter ++;
			total_num ++;
			for(iter1=nums1.begin();iter1<nums1.end();++iter1){
				if(*iter1 != last_num){
					last_num = *iter1;
					*iter = last_num;
					iter ++;
					total_num ++;
				}
			}
			return total_num;
	    }
	};
	// The code under blow is used for test
	int main() {
		vector<int> nums;
		vector<int>::iterator iter;
		nums.push_back(1);
		nums.push_back(2);
		nums.push_back(2);
		nums.push_back(3);
		
		Solution s;
		int total_num = s.removeDuplicates(nums);
		cout<<"total_num="<<total_num<<endl;
		for(iter=nums.begin();iter<nums.end();++iter){
			cout<<*iter<<endl;
		}
		system("pause");
		return 0;
	}



# Note
To simplify the problem, I copy the useful values from nums to nums1. Then, traverse the nums1, copy the value which is differet from the last one to nums. 
