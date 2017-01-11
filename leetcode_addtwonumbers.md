title: LeetCode Add Two Numbers
date: 2015-01-24 21:21:18
tags: leetcode
---

# Description
You are given two linked lists representing two non-negative numbers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8

The original problem is [here](https://oj.leetcode.com/problems/add-two-numbers/ "here"):  
<!--more-->

# My Solution
I solve this problem in Java, as below:
	

	 /**
	 * Definition for singly-linked list.
	 * public class ListNode {
	 *     int val;
	 *     ListNode next;
	 *     ListNode(int x) {
	 *         val = x;
	 *         next = null;
	 *     }
	 * }
	 */
	public class Solution {
	    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
	        int carry = 0;
	        int value = 0;
	        int count = 0;
	        ListNode result = null, l3 = null;
	
	        while(l1 != null || l2 != null)
	        {
	            if(l1 == null)
	                l1 = new ListNode(0);
	            if(l2 == null)
	                l2 = new ListNode(0);
	            
	            if(count == 0)
	            {
	                l3 = new ListNode(0);
	                result = l3;
	            }
	            else
	            {
	                l3.next = new ListNode(0);
	                l3 = l3.next;
	            }
	            if(carry == 1)
	            {
	                l3.val = 1;
	            }
	            value = l1.val + l2.val + carry;
	            if(value >= 10)
	            {
	                value = value%10;
	                carry = 1;
	            }
	            else
	                carry = 0;
	            l3.val = value;
	
	            if(carry == 1)
	            {
	                l3.next = new ListNode(1);
	            }
	
	            l1 = l1.next;
	            l2 = l2.next;
	            count ++;
	        }
	
	        return result;
	    }
	}



# Note
Because of the two numbers are stored in two Linked lists, the addition is computed for each digit, so don't foget the carry(进位). Additionly, the two linked lists may have different lengths!
