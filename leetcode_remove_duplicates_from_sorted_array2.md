title: LeetCode Remove Duplicates from Sorted Array
date: 2015-06-19 09:37:25
tags: leetcode
---

# Description
Follow up for "Remove Duplicates":
What if duplicates are allowed at most twice?

For example,
Given sorted array nums = [1,1,1,2,2,3],

Your function should return length = 5, with the first five elements of nums being 1, 1, 2, 2 and 3. It doesn't matter what you leave beyond the new length.

The original problem is [here](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/RemoveDuplicatesFromSortedArray2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*
	*Remove Duplicates from Sorted Array 2
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
	    	int size = nums.size();
			if(size <= 2)
	    		return size;
			vector<int> result;
	        int lastNum = nums[0];
	        int totalNum = 1;
	        int repeatNum = 0;
	        
	        result.push_back(nums[0]);
	        for(int i=1;i<size;i++){
	        	if(nums[i] == lastNum){
	        		repeatNum ++;
	        		if(repeatNum <= 1){
	        			result.push_back(nums[i]);
	        			totalNum ++;
	        		}
	        	}
	        	else{
	        		repeatNum = 0;
	        		lastNum = nums[i];
	        		result.push_back(nums[i]);
					totalNum ++;
	        	}
	        }
	        nums =  result;
	        return totalNum;
	    }
	};
	// The code under blow is used for test
	int main() {
		vector<int> nums;
		vector<int>::iterator iter;
		nums.push_back(1);
		nums.push_back(1);
		nums.push_back(1);
		//nums.push_back(1);
		
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
A new array is used to save the valid numbers. Then, traverse the nums, copy the value which is differet from the last two to the new array. 
