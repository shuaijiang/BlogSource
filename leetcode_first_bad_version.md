title: LeetCode First Bad Version
date: 2015-09-08 15:27:12
tags: leetcode
---

# Description
You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.

Suppose you have n versions [1, 2, ..., n] and you want to find out the first bad one, which causes all the following ones to be bad.

You are given an API bool isBadVersion(version) which will return whether version is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.

The original problem is [here](https://leetcode.com/problems/first-bad-version/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/FirstBadVersion.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*First Bad Version 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<math.h>
	#include<stdlib.h>
	using namespace std;
	
	// Forward declaration of isBadVersion API.
	bool isBadVersion(int version){
		//if(version >= 1702766719)
		if(version >= 2)
			return true;
		return false;
	}
	
	class Solution {
	public:
	    int firstBadVersion(int n) {
	        double low = 1, high = n;
	        double middle = 0;
	        int m;
	        while(low < high){
	        	middle = (low + high) / 2;
	        	m =  (int)floor(middle);
	        	if(isBadVersion(m))
	        		high = m;
	        	else
	        		low = m + 1;
	        }
	        if(low == high)
	        	return low;
	    }	
	};
	
	int main() {
		int n = 2; //2126753390;
		Solution s;
		int res = s.firstBadVersion(n);
		cout<<res<<endl;
		system("pause");
		return 0;
	}

# Note
In the solution, binary search is used. You should make sure that the value is not extend the scale of the 32bit int. 
