title: LeetCode Find Peak Element
date: 2015-03-30 23:11:09
tags: leetcode
---

# Description
A peak element is an element that is greater than its neighbors.

Given an input array where num[i] ≠ num[i+1], find a peak element and return its index.

The array may contain multiple peaks, in that case return the index to any one of the peaks is fine.

You may imagine that num[-1] = num[n] = -∞.

For example, in array [1, 2, 3, 1], 3 is a peak element and your function should return the index number 2.

The original problem is [here](https://leetcode.com/problems/find-peak-element/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/Find_Peak_Element.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Find Peak Element
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	using namespace std;
	
	class Solution {
	public:
	    int findPeakElement(const vector<int> &num) {
	        int count = 0;
	        if(num.size() > 1)
	        {
	        	for(count=0;count<num.size();++count)
		        {
		        	if(count == 0)
		        	{
		        		if(num[count] > num[count+1])
		        			return count;
		        	}
		        	else if(count == num.size()-1)
		        	{
		        		if(num[count] > num[count-1])
		        			return count;
		        	}
		        	else
		        	{
		        		if(num[count] > num[count-1] && num[count] > num[count+1]) 
		        			return count;
		        	}
		        }
	        }
	        else
	        	return count;
	    }
	};
	
	int main() 
	{
		Solution s;
		int array[] = {1,2,3,1};
		vector<int> num;
		for(int count=0;count<4;++count)
		{
			num.push_back(array[count]);
		}
		vector<int>::iterator iter;
		for(iter=num.begin();iter<num.end();++iter)
			cout<<*iter<<endl;
		int index = s.findPeakElement(num);
		cout<<"index="<<index<<endl;
	}

# Note:
This problem is easy, the only thing we need to note is the begining and end of the number;
