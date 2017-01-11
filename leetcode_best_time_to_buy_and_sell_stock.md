title: LeetCode Best Time to Buy and Sell Stock 
date: 2015-07-12 11:23:55
tags: leetcode
---


# Description
Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.

The original problem is [here](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/BestTimeToBuyAndSellStock.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Best Time to Buy and Sell Stock 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int maxProfit(vector<int>& prices) {
	        int size = prices.size();
	        if(size<=0)
	        	return 0;
	        int maxPro = 0, profit=0;
	        int start=0, end=0;
	        for(int i=1;i<size;i++){
	        	profit = prices[i] - prices[start];
	        	if(maxPro < profit)
	        		maxPro = profit; 
				if(profit <= 0)
					start = i;
	        }
	        return maxPro;
	    }
	};

# Note
Traversal the prices, and compute the profit by prices[i]-prices[start], if the profit is larger than the max profit, then let modify the max profit. If the profit is less than zero, then modify the time when to buy.
