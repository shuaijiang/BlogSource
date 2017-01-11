title: LeetCode Best Time to Buy and Sell Stock 3
date: 2015-08-04 15:09:34
tags: leetcode
---


# Description
Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete at most two transactions.

Note:
You may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).

The original problem is [here](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/BestTimeToBuyAndSellStock3.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Best Time to Buy and Sell Stock III
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int maxProfit(vector<int>& prices) {
	        int size = prices.size();
	        if(size<=0)
	        	return 0;
	        vector<int> currProfit(size,0);
	        int maxPro = 0;
	        int result=0;
	        int minPrice = prices[0];
	        for(int i=1;i<size;i++){
	        	minPrice = min(prices[i-1], minPrice);
	        	if((prices[i]-minPrice) > maxPro)
	        		maxPro = prices[i] - minPrice;
				currProfit[i] = maxPro;
	        }
	        maxPro = 0;
	        int maxPrice = prices[size-1];
	        for(int i=size-2;i>=0;i--){
	        	maxPrice = max(prices[i+1], maxPrice);
				if((maxPrice - prices[i]) > maxPro)
					maxPro = maxPrice - prices[i];
				if(maxPro + currProfit[i] > result)
					result = maxPro + currProfit[i];
	        }
	        return result;
	    }
	};

# Note
To solve the problem, first traversal the prices from head to tail and keep the maxProfit of the current price to an array. Then, traversal the prices from tail to head, and get the maxProfit from current price to the maxprice.

Finally, get the max profit by add the two part of the profit. 
