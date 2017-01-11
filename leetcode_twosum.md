title: LeetCode Two Sum
date: 2015-01-20 20:24:46
tags: leetcode
---

# Description
Given an array of integers, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2. Please note that your returned answers (both index1 and index2) are not zero-based.

You may assume that each input would have exactly one solution.

Input: numbers={2, 7, 11, 15}, target=9
Output: index1=1, index2=2

The original problem is [here](https://oj.leetcode.com/problems/two-sum/ "here"):  
<!--more-->

# My Solution
I solve this problem in Java, as below:
	

	import java.util.HashMap; 
	public class Solution {
	    public int[] twoSum(int[] numbers, int target) {
	        int[] index = new int[2];
	        index[0] = -1;
	        index[1] = -1;
	        HashMap<Integer,Integer> map = new HashMap<Integer,Integer>();
	        int len = numbers.length;
	        for(int i=0;i<len;i++)
	        {
	            Integer value = target - numbers[i];
	            map.put(value,i+1);
	        }
	        for(int i=0;i<len;i++)
	        {
	            Integer gap = target - numbers[i];
	            Integer index2 = map.get(gap);
	            if(index2 != null && index2 != i + 1)
	            {
	                index[0]=i+1;
	                index[1]=index2;
	                return index;
	            }
	        }
	        return index;
	    }
	}

# Note
One more 'simple' solution is just traversal the array in two nests, but it will take about $O(N^2)$, which exceeds the time. So another way is using Hash(or HashMap in java), keep the difference value between target and number, then you can get it without costing many time. This way just take about $O(N)$.
