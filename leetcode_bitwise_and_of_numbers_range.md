title: LeetCode Bitwise AND of Numbers Range
date: 2015-10-19 15:21:42
tags: leetcode
---

# Description
Given a range [m, n] where 0 <= m <= n <= 2147483647, return the bitwise AND of all numbers in this range, inclusive.

For example, given the range [5, 7], you should return 4.

The original problem is [here](https://leetcode.com/problems/bitwise-and-of-numbers-range/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/BitwiseANDofNumbersRange.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Bitwise AND of Numbers Range
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<math.h>
	using namespace std;
	
	class Solution {
	public:
	    int rangeBitwiseAnd(int m, int n) {
	        int res = m;
	        if(m==0)
	            return 0;
			int move = 0; // the number of the move steps
	        while(m!=n){
	            m = m>>1;
	            n = n>>1;
	            move +=1;
	        }
	        return m << move;  // if m is 0, then the result is also 0
	    }
	};
	int main(){
		Solution s;
		//int m = 600000000, n = 2147483645;
		int m = 2147483646, n = 2147483647;
		int res = s.rangeBitwiseAnd(m, n);
		cout<<res<<endl;
		return 0;
	}

# Note
直接采用从m到n遍历，使用&位运算符进行位运算，原理是这样的，但是会超时。因为m<n,将该范围内的所有数进行与运算后，如果某一个位的为1，则m和n一定在该位的所有更高的位上要不全为零、要不全为1，否则中间的数会存在该位为0的情况。

通过位移运算，更加快速找到高位全相等的情况。如果此时高位全为0，则结果为0；如果高位全为1，则结果为将从该位到低位全设置为0的结果。
