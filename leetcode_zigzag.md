title: Leetcode: ZigZag Conversion
date: 2015-03-15 08:48:58
tags: leetcode
---

#Description
The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

P   A   H   N
A P L S I I G
Y   I   R
And then read line by line: "PAHNAPLSIIGYIR"
Write the code that will take a string and make this conversion given a number of rows:

string convert(string text, int nRows);
convert("PAYPALISHIRING", 3) should return "PAHNAPLSIIGYIR".

The original problem is [here](https://leetcode.com/problems/zigzag-conversion/ "here"):  
<!--more-->

#My Solution
I solve this problem in Python, as below:
	

	class Solution:
		# @return a string
	    def convert(self, s, nRows):
	        new_str = [""]* nRows
	        count = 0
	        direct = 1
	        for i in range(len(s)):
	            if(direct == 1):
	                new_str[count] += s[i]
	                if count == nRows-1:
	                    direct = 0
	                    count -= 1
	                    if count<=0:
	                        count = 0
	                else:
	                    count += 1
	            else:
	                new_str[count] += s[i]
	                if count == 0:
	                    direct = 1
	                    count += 1
	                    if count>=nRows:
	                        count = nRows-1
	                else:
	                    count -= 1
	        new_s=""
	        for j in range(len(new_str)):
	            new_s += new_str[j]
	        return new_s

#Note
First of all, you should know what is "ZigZag". In this problem, we can consider it as one person runs between two "point": run from start to end, and then run back.

Secondly, when we convert the string to "ZigZag", how to deal the begin and end of each column should under the consider. 

And other special conditions should also be considered, such as when nRows=1, and so on.