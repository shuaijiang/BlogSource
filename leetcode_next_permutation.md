title: LeetCode Next Permutation
date: 2015-07-24 15:12:44
tags: leetcode
---

# Description
Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.

If such arrangement is not possible, it must rearrange it as the lowest possible order (ie, sorted in ascending order).

The replacement must be in-place, do not allocate extra memory.

Here are some examples. Inputs are in the left-hand column and its corresponding outputs are in the right-hand column.
1,2,3 → 1,3,2
3,2,1 → 1,2,3
1,1,5 → 1,5,1

The original problem is [here](https://leetcode.com/problems/next-permutation/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/NextPermutation.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Next Permutation
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
	    void nextPermutation(vector<int>& nums) {
	        int size=nums.size();
	        if(size<=1)
	        	return;
	        int indexBegin=-1, indexLarge; 
			for(int i=size-1;i>0;i--){
	        	if(nums[i]>nums[i-1]){
	        		indexBegin = i;
	        		break;
	        	}	
	        }
	        if(indexBegin == -1){
	        	sort(nums.begin(),nums.end());
	        	return;
	        }
	        int minNum = nums[indexBegin];
	        indexLarge = indexBegin;
	        for(int i=indexBegin;i<size;i++){
	        	if(nums[i]>nums[indexBegin-1] && nums[i]<=minNum){
	        		minNum = nums[i];
					indexLarge = i;
	        	}
	        }
			int temp = nums[indexBegin-1];
			nums[indexBegin-1] = nums[indexLarge];
			nums[indexLarge] = temp;
			
			sort(nums.begin()+indexBegin,nums.end());
			return;
	    }
	};
	//The code under below is used for test
	int main(){
		Solution s;
		vector<int> nums;
		nums.push_back(1);
		nums.push_back(2);
		nums.push_back(3);
		
		s.nextPermutation(nums);
		for(int i=0;i<nums.size();i++){
			cout<<nums[i]<<endl;
		}
		system("pause");
		return 0;
	}


# Note
To solve the problem, first, find the first position which the nums[i] is larger than nums[i-1] from end to begin. Second, exchange the nums[i-1] with the number from the range from the position to the end, and the number is smallest but larger than nums[i-1]. Finally, sort the range from the position to the end.  
