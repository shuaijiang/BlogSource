title: LeetCode Candy
date: 2015-07-27 21:30:28
tags: leetcode
---

# Description
There are N children standing in a line. Each child is assigned a rating value.

You are giving candies to these children subjected to the following requirements:

- Each child must have at least one candy.

- Children with a higher rating get more candies than their neighbors.

What is the minimum candies you must give?

The original problem is [here](https://leetcode.com/problems/candy/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/Candy.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:	

	/*
	*Candy  
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int candy(vector<int>& ratings) {
	        vector<int> candies;
	        int size = ratings.size();
	        for(int i=0;i<size;i++)
	        	candies.push_back(1);
	        for(int i=1;i<size;i++){
	        	if(ratings[i] > ratings[i-1])
	        		candies[i] = candies[i-1] + 1;
	        }
	        for(int i=size-2;i>=0;i--){
	        	if(ratings[i] > ratings[i+1] && candies[i] <= candies[i+1])
	        		candies[i] = candies[i+1] + 1;
	        }
	        int result = 0;
	        for(int i=0;i<size;i++)
	        	result += candies[i];
	        return result;
	    }
	};

# Note
To solve this problem, vector candies is used to save the number of candies of children. 

First, init every number in the vector to 1. 

Second, traversal the ratings from head to tail, if the ratings[i] is larger than ratings[i-1], then candies[i] = candies[i-1] + 1.  

Third, traversal the ratings from tail to head, if ratings[i] is larger than ratings[i+1] and the candies[i] is not larger than candies[i+1], then candies[i] = candies[i+1]+1.

Finally, return the sum of the candies.
