title: LeetCode: Longest Substring Without Repeating Characters
date: 2015-01-25 18:29:50
tags: leetcode
---
#Description
Given a string, find the length of the longest substring without repeating characters. For example, the longest substring without repeating letters for "abcabcbb" is "abc", which the length is 3. For "bbbbb" the longest substring is "b", with the length of 1.

The original problem is [here](https://oj.leetcode.com/problems/longest-substring-without-repeating-characters/ "here"):  
<!--more-->

#My Solution
	import java.util.HashMap;
	public class Solution {
    	public int lengthOfLongestSubstring(String s) {
	        HashMap<Integer,Integer> substr = new HashMap<Integer,Integer>();
	        HashMap<Integer,Integer> lengthHash = new HashMap<Integer,Integer>();
	        int count = 0 , start = 0;
	        int length = 0;
	        int max = 0;
	        for(count=0;count<s.length();count++)
	        {
	            char ch_real = s.charAt(count);
	            int ch = (int)ch_real;
	            if(substr.get(ch) == null || substr.get(ch) < start)
	            {
	                length += 1;
	                substr.put(ch,count);
	            }
	            else
	            {
	                lengthHash.put(length,1);
	                length = count - substr.get(ch);
	                start = substr.get(ch) + 1;
	                substr.put(ch,count);
	            }
	        }
	        lengthHash.put(length,1);
	        for(Object obj:lengthHash.keySet())
	        {
	            Object key = obj;
	            Integer value = (Integer)key;
	            if(value > max)
	                max = value;
	        }
	        return max;
	    }
	}

#Note
In my solution, I traversal the string once. During the traversal, we can find each substring and the length of it. Finally, we can get maximum of the lengths. 