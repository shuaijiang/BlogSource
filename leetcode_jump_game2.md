title: LeetCode Jump Game 2
date: 2015-08-03 09:48:47
tags: leetcode
---


# Description
Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Your goal is to reach the last index in the minimum number of jumps.

For example:
Given array A = [2,3,1,1,4]

The minimum number of jumps to reach the last index is 2. (Jump 1 step from index 0 to 1, then 3 steps to the last index.)

The original problem is [here](https://leetcode.com/problems/jump-game-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/JumpGame2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Jump Game II
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int jump(vector<int>& nums) {
	        int size = nums.size();
	        int step = 0;
	        if(size <= 1)
	        	return step;
	        
	        int currIndex = 0;
	        int nextIndex = nums[0];
	        while(currIndex <= nextIndex && currIndex < size){
	        	int temp = nextIndex;
				for(int j=currIndex;j<=temp && j<size;j++){
					if(nums[j] + j > nextIndex){		
						nextIndex = nums[j] + j;
					}	
				}
				step ++;
				currIndex = temp + 1;
	        }
	        return step;
	    }
	};
	
	int main() {
		Solution s;
		vector<int> nums;
		nums.push_back(1);
		nums.push_back(2);
		
		int result = s.jump(nums);
		cout<<"result="<<result<<endl;
		system("pause");
		return 0;
	}



# Note
To solve the problem,  Greedy algoritym is used. It is similar to [Jump Game](https://leetcode.com/problems/jump-game/).
