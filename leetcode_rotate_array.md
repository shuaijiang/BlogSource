title: Leetcode: Rotate Array 
date: 2015-03-20 14:05:46
tags: leetcode
---

#Description
Rotate an array of n elements to the right by k steps.

For example, with n = 7 and k = 3, the array [1,2,3,4,5,6,7] is rotated to [5,6,7,1,2,3,4].

Note:
Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.

The original problem is [here](https://leetcode.com/problems/rotate-array/  "here"):  
<!--more-->

#My Solution
I solve this problem in Python, as below:

	class Solution:
		# @param nums, a list of integer
		# @param k, num of steps
		# @return nothing, please modify the nums list in-place.
		def rotate(self, nums, k):
			total_num = len(nums)
			temp_nums = nums[:]
			if(total_num <= k):
				k =  k % total_num
			begin_count = total_num - k
			for i in range(0,k):
				nums[i] = temp_nums[begin_count+i]
			for i in range(k,total_num):
				nums[i] = temp_nums[i-k]
	
			#return nums

		#The codes Under below is used for running
		#Don't submit them
		#nums = [1,2,3,4,5]
		#k = 3
		#S = Solution()
		#S.rotate(nums,k)
		#print nums

#Note
One point should be noted is when k is larger than the length of the array, we should compute the modulus of k to the array length.