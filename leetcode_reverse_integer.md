title: Leetcode: Reverse Integer 
date: 2015-03-15 20:37:46
tags: leetcode
---

#Description
Reverse digits of an integer.

Example1: x = 123, return 321
Example2: x = -123, return -321

The original problem is [here](https://leetcode.com/problems/reverse-integer/  "here"):  
<!--more-->

#My Solution
I solve this problem in Python, as below:
	
	class Solution:
	    # @return an integer
	    def reverse(self, x):
	        max_int =  2147483647
	        min_int = -2147483648
	        y = "0"
	        flag = "";
	        if x < 0:
	            flag = "-"
	            x =-x
	        else:
	            flag = ""
	        while(x > 0) :
	            y += str(x%10)
	            x = x/10
	        y = flag + y
	        y = int(y)
	        if(y>max_int):
	            y = 0
	        if(y<min_int):
	            y = 0
	        return y

#Note
There maybe only one problem should be noted is "overflow". The integer is 32-bit number, we should ensure the result is not beyond the scope -2147483648 ~ 2147483647. If so, the result should be zero.