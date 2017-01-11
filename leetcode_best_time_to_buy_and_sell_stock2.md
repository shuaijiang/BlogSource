title: LeetCode Best Time To Buy And Sell Stock 2
date: 2015-07-09 22:18:39
tags: leetcode
---


# Description
Say you have an array for which the i(th) element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (ie, buy one and sell one share of the stock multiple times). However, you may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).

The original problem is [here](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/BestTimeToBuyAndSellStock2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*Best Time to Buy and Sell Stock II
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int maxProfit(vector<int>& prices) {
	       if(prices.size()<=0)
	       	return 0;
		   int profit = 0;
	
		   for(int i=1;i<prices.size();i++){
		   		int diff = prices[i]-prices[i-1];
		   		if(diff>=0)
		   			profit += diff;
		   }
		   		
		   	return profit;
	    }
	};


# Note
To solve the problem, I compute the difference between the current price and the last price. If the difference is non-negative, then add to the profit. 
