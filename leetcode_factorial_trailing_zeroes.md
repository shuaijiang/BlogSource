title: LeetCode Factorial Trailing Zeroes
date: 2015-03-30 23:10:04
tags: leetcode
---
# Description
Given an integer n, return the number of trailing zeroes in n!.

Note: Your solution should be in logarithmic time complexity.

The original problem is [here](https://leetcode.com/problems/factorial-trailing-zeroes/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/Factorial_Trailing_Zeroes.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Factorial Trailing Zeroes
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	using namespace std;
	
	class Solution {
	public:
	    int trailingZeroes(int n) 
		{
	        int zeros = 0;
			int factor = 5;
	        while(n)
	        {
				
				zeros = zeros + n/factor;
				n = n/factor;
	        }
			return zeros;
		}
		/* The code below exceed the time
	    int trailingZeroes(int n) 
		{
	        int zeros = 0;
			int factor = 5;
	        while(factor <= n)
	        {
			
				zeros = zeros + n/factor;
				factor = factor * 5;
				if(factor >= 2147483647)
					return zeros;
	        }
			return zeros;
		}
		*/
	};
	//The code under below is used for test
	int main()
	{
	
		Solution s;
		int n = 2147483647;
		cout<<"n="<<n<<endl;
		int zeros = s.trailingZeroes(n);
		cout<<zeros<<endl;
		system("pause"); 
	}

# Note
One thing need to be noted is the time complexity. Because the trailing zeros are produced by 5 * 2, and the number of 5 is more than 2, so we just need point the number of 5. N=|_ 5^j _|, we just need compute the j.
