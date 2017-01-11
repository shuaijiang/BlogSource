title: LeetCode Climbing Stairs
date: 2015-07-10 10:13:12
tags: leetcode
---


# Description
You are climbing a stair case. It takes n steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

The original problem is [here](https://leetcode.com/problems/climbing-stairs/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ClimbingStairs.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Climbing Stairs  
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int climbStairs(int n) {    		
	    	vector<int> vec;
			vec.push_back(1);
			vec.push_back(1);
	        if(n<=1)
	        	return vec[n];
	        for(int i=2;i<=n;i++){
	        	int num = vec[i-1] + vec[i-2];
	        	vec.push_back(num);
	        }
	        return vec[n];
	    }
	};
	//The code below is used for test
	int main()
	{
		int n = 44;
		Solution s;
		int result = s.climbStairs(n);
		cout<<"result="<<result<<endl;
		system("pause");
		return 0;
	}



# Note
To solve the problem, I use a vector to save the result of every step, and the distinct ways of the i(th) step is the sum of the i-1 and i-2 steps. 
