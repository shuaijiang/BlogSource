title: LeetCode Excel Sheet Column Number
date: 2015-04-05 21:13:49
tags: leetcode
---

# Description
Related to question Excel Sheet Column Title

Given a column title as appear in an Excel sheet, return its corresponding column number.

For example:

    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 

The original problem is [here](https://leetcode.com/problems/excel-sheet-column-number/ "Problem").

My code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ExcelSheetColumnNumber.cpp "Code").

<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Excel Sheet Column Number 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<math.h>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int titleToNumber(string s) {
	    	int num = 0;
	    	int bit_num = 0;
	        int len = s.size();
			for(int count=len-1;count>=0;count--,bit_num ++)
			{
				int diff = s[count]-'A' + 1;
				num += diff * pow(26,bit_num);
			} 
			return num;
	    }
	}; 
	//the codes below is used for test
	int main()
	{
		
		string str("AB");
		Solution s;
		int num = s.titleToNumber(str);
		cout<<num<<endl;
		system("pause");
	}

# Note
This problem is similar to conver  binary to decimal.
