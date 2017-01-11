title: LeetCode Happy Number
date: 2015-06-25 16:50:52
tags: leetcode
---



# Description
Write an algorithm to determine if a number is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

Example: 19 is a happy number

12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1

The original problem is [here](https://leetcode.com/problems/happy-number/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/HappyNumber.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:


	/*
	*Happy Number
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<string.h>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    bool isHappy(int n) {
	    	map<int,int> myMap;
	    	myMap[n] = 1;
	        while(n!=1){
	        	n = squareSum(n);
	        	if(n == 1)
	        		break;
	        	if(myMap.find(n)==myMap.end()){
	        		myMap[n] = 1;
	        	}
	        	else{
	        		return false;
	        	}
	        }
	        return true;
	    }
	    int squareSum(int n){
	    	vector<int> vec;
	    	int elem = 0, sum = 0;
	    	
	    	while(n>0){
	    		elem = n % 10;
	    		vec.push_back(elem);
	    		n = n / 10;
	    	}
	    	for(int count=0;count<vec.size();++count){
	    		sum += vec[count] * vec[count];
	    	}
	    	return sum;
	    }
	};

# Note
To solve the problem, we should compute the square sum of each digits of the number. It is important that when to finish the procedure of computation of the square sum. I use a hash(map in C++) to save the sum computed before, and when a new sum come, if we can get it from the hash, then we know that a circle exists, and the number is not a happy number. However, if the sum is equal to 1, then it is a happy number. 
