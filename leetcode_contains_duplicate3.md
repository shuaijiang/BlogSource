title: LeetCode Contains Duplicate 3
date: 2015-10-19 14:10:34
tags: leetcode
---

# Description
Given an array of integers, find out whether there are two distinct indices i and j in the array such that the difference between nums[i] and nums[j] is at most t and the difference between i and j is at most k.

The original problem is [here](https://leetcode.com/problems/contains-duplicate-iii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ContainsDuplicate3_set.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Contains Duplicate III
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<set>
	using namespace std;
	
	class Solution {
	public:
	    bool containsNearbyAlmostDuplicate(vector<int>& nums, int k, int t) {
	        int size = nums.size();
	        if(size<=1 || k<=0)
	        	return false;
	        set<long> mySet; // windows which has k elements at most
	        int low = 0;
	        for(int i=0;i<size;++i){
	        	if(mySet.size() > k){
					mySet.erase(nums[low++]);
				}
	        	auto target = mySet.lower_bound((long)nums[i] - (long)t); // the first element which target >= nums[i]-t
	        	if(target != mySet.end() && *target <= (long)nums[i]+(long)t) //  nums[i] + t <= target <= nums[i] + t
	        		return true;
	        	mySet.insert(nums[i]);
	        }
			return false;
	    }
	};
	int main(){
		Solution s;
		vector<int> nums(3,0);
		nums[0]=1;nums[1]=3;nums[2]=1;
		int k = 1; int t =1;
		bool res = s.containsNearbyAlmostDuplicate(nums, k, t);
		cout<<res<<endl;
		return 0;
	}

# Note
需要维护一个长度为k的窗，使用set<long>来实现。遍历数组vector<int>nums，在窗中寻找大于nums[i]-t的最小数，如果发现该数，并且该数小于nums[i]-t，则返回true。

即如果在窗中存在一个数 在区间[nums[i]-t, nums[i]+t]中，则返回true。
