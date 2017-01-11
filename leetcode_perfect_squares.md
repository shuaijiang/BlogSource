title: LeetCode Perfect Squares
date: 2015-09-13 21:27:24
tags: leetcode
---

# Description
Given a positive integer n, find the least number of perfect square numbers (for example, 1, 4, 9, 16, ...) which sum to n.

For example, given n = 12, return 3 because 12 = 4 + 4 + 4; given n = 13, return 2 because 13 = 4 + 9.

The original problem is [here](https://leetcode.com/problems/perfect-squares/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/PerfectSquares.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Perfect Squares
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<math.h>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int numSquares(int n) {
	    	if(n <= 0)
	    		return -1;
	    	if(n == 1)
	    		return 1;
	        vector<int> square;
	        vector<int> nums;
	        nums.push_back(0);
	        nums.push_back(1);
	        int num = 1;
			while(num*num <= n){
				square.push_back(num*num);
				num ++;
			}
			
			int index = 0;
			for(int i=2;i<=n;i++){
				index = sqrt(i);
				int factor = square[index-1];
				if(factor == i) {
					nums.push_back(1);
					continue;
				}
				int minCount = nums[i-factor] + 1;
				for(int j=index-2;j>=0;j--){
					factor = square[j];
					int count = nums[i - factor] + 1;
					minCount = min(minCount, count);
				}
				cout<<i<<" "<<minCount<<endl;
				nums.push_back(minCount);			
			}
			return nums[n];
	    }
	};
	int main(){
		Solution s;
		int n = 100;
		int result = s.numSquares(n);
		cout<<"result="<<result<<endl;
		system("pause");
		return 0;
	}



# Note
采用动态规划解决.从1到n,依次计算每个数需要的最小平方数。对于一个数num，找到所有比它小的平方数S_i，比num小S_i的数所对应的数目再加一就是 num的数目, 再从这么数目中求最小的数目。这样就可以得到n的最小数目。
