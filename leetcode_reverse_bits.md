title: LeetCode Reverse Bits 
date: 2015-03-22 22:18:25
tags: leetcode
---

# Description
Reverse bits of a given 32 bits unsigned integer.

For example, given input 43261596 (represented in binary as 00000010100101000001111010011100), return 964176192 (represented in binary as 00111001011110000010100101000000).

The original problem is [here](https://leetcode.com/problems/reverse-bits/  "here"):  
<!--more-->

# My Solution
I solve this problem in Python, as below:

	class Solution:
	    # @param n, an integer
	    # @return an integer
		def reverseBits(self, n):
			bits = [0] * 32;
			rev_bits = [0] * 32;
			bits = self.integer2binary(n)
			for i in range(len(bits)):
				rev_bits[i] = bits[31-i]
			rev_n = self.binary2integer(rev_bits)
			return rev_n
		def integer2binary(self,n):
			bits = [0]*32
			i = 31
			while(n>0):
				bits[i] = n % 2
				n = n/2
				i -=1
			return bits
		def binary2integer(self,bits):
			n = 0
			bits_len = len(bits)
			for i in range(len(bits)):
				n += bits[i]*pow(2,bits_len-i-1)
			return n

	
	#The code under below is used for test
	#n=43261596
	#S = Solution()
	#print S.reverseBits(n)

# Note
This problem can be parted as two parts: one is integer2binary and the other is binary2integer. Then it is easy to solve this problem.
