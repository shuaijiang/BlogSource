title: LeetCode Longest Consecutive Sequence
date: 2015-07-23 10:01:48
tags: leetcode
---

# Description
Given an unsorted array of integers, find the length of the longest consecutive elements sequence.

For example,
Given [100, 4, 200, 1, 3, 2],
The longest consecutive elements sequence is [1, 2, 3, 4]. Return its length: 4.

Your algorithm should run in O(n) complexity.

The original problem is [here](https://leetcode.com/problems/longest-consecutive-sequence/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/LongestConsecutiveSequence.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Longest Consecutive Sequence 
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
	    int longestConsecutive(vector<int>& nums) {
	    	int longestNum = 0, num;
	    	int size = nums.size();
			if(size<=0)
		   		return longestNum;
		   	if(size == 1)
		   		return 1;
			sort(nums.begin(),nums.end());
			
			longestNum = 1;
			num = 1;
			for(int i=1;i<size;i++){
				if(nums[i]-nums[i-1] == 0)
					;
				else if(nums[i]-nums[i-1] == 1)
					num ++;
				else
					num = 1;
				if(num > longestNum)
					longestNum = num;
			}
			return longestNum;
	    }
	};
	// the code under below is used for test
	int main(){
		Solution s;
		vector<int> nums;
		nums.push_back(0);
		nums.push_back(-1);
		
		int num = s.longestConsecutive(nums);
		cout<<"num="<<num<<endl;
		system("pause");
		return 0;
	}


# Note
First, sort the vector. Then count the consecutive sequence, select the largest length. Note the equal number doesn't contribute to the length.
