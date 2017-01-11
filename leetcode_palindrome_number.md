title: LeetCode Ppalindrome Number
date: 2015-06-21 11:34:36
tags: leetcode
---


# Description
Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this in place with constant memory.

For example,
Given input array nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively. It doesn't matter what you leave beyond the new length.

The original problem is [here](https://leetcode.com/problems/palindrome-number/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/PalindromeNumber.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Palindrome Number  
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<math.h>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    bool isPalindrome(int x) {
	    	if(x < 0)
	    		return false;
	    	int y = x;
			int len = numberLength(y);
			if(len == 1)
				return true;
			int high_num, low_num;
			int high_divisor, low_divisor;
			high_divisor = pow(10,len-1);
			low_divisor  = 10;
			while(high_divisor >= low_divisor){
				high_num = y / high_divisor;
				low_num  = y % low_divisor; 
				if(high_num != low_num)
					return false;
				y = y - high_num * high_divisor;
				y = y / low_divisor;
				high_divisor = high_divisor / 100;
			}
			
			return true;
	    }
	    int numberLength(int x){
	    	int y = x;
			int len = 0;
			while(y>0){
				y = y / 10;
				len ++;
			}
			return len;
	    }
	};
	//the code under below is for test
	int main(){
		Solution s;
		int x = -2147447412;
		int len = s.numberLength(x);
		bool p = s.isPalindrome(x);
		cout<<"len="<<len<<endl;
		cout<<"p="<<p<<endl;
		system("pause");
		return 0;
	}



# Note
To solve the problem, we just find the high number and the low number of x. Then compare them, if the same go to the next, else return false. Before next step, we should remove the high number and low number of x. 
