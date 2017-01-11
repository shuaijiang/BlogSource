title: LeetCode Merge Sorted Array
date: 2015-06-19 09:37:25
tags: leetcode
---

# Description
Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

Note:
You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2. The number of elements initialized in nums1 and nums2 are m and n respectively.

The original problem is [here](https://leetcode.com/problems/merge-sorted-array/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/MergeSortedArray.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	#include<iostream>
	#include<math.h>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
	    	vector<int> nums3;
	        vector<int>::iterator  iter1, iter2,iter3;
	        int count=0,count1=0, count2=0;
	        int temp = 0;
	        iter1=nums1.begin();
			for(count1=0;count1<m;count1++){
				nums3.push_back(*iter1);
				iter1++;
			}
			iter1=nums1.begin();
			iter2=nums2.begin();
			iter3=nums3.begin();
			count1=0; 
	        for(;iter2<nums2.end()&&iter3<nums3.end();){
	        	cout<<*iter3<<" "<<*iter2<<endl;
	        	if(*iter3 <= *iter2){
					*iter1 = *iter3;
					iter1 ++;
					iter3 ++;
	        	}
	        	else{
					*iter1 = *iter2;
	        		iter1 ++;
	        		iter2 ++;
	        	}
	        }
	        while(iter2<nums2.end()){
	        	*iter1 = *iter2;
	        	iter1++;
	        	iter2++;
	        }
	        while(iter3<nums3.end()){
	        	*iter1 = *iter3;
	        	iter1++;
	        	iter3++;
	        }
	    }
	};
	// The code under blow is used for test
	int main()
	{
		vector<int> nums1;
		vector<int> nums2;
		vector<int>::iterator iter;
		Solution s;
		nums1.push_back(2);
		nums1.push_back(0);
		nums2.push_back(1);
		s.merge(nums1,1,nums2,1);
		for(iter=nums1.begin();iter<nums1.end();++iter){
			cout<<*iter<<endl;
		}
		system("pause");
		return 0;
	}



# Note
To simplify the problem, I copy the useful values from nums1 to nums3. Then, compare the nums2 and nums3, and using "merge sort" algorithm to get the sorted array nums1. 
