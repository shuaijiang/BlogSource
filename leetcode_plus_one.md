title: LeetCode Plus One
date: 2015-06-21 23:31:12
tags: leetcode
---


# Description
Given a non-negative number represented as an array of digits, plus one to the number.

The digits are stored such that the most significant digit is at the head of the list.

The original problem is [here](https://leetcode.com/problems/plus-one/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/PlusOne.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Plus One
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<math.h> 
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    vector<int> plusOne(vector<int>& digits) {
	    	vector<int> new_digits,temp_digits;
	    	if(digits.size() <= 0){
	    		new_digits.push_back(1);
	    		return new_digits;
	    	}
	        vector<int>::iterator iter;
	        vector<int>::reverse_iterator reiter;
	        int flag = 0;
	        for(reiter=digits.rbegin();reiter<digits.rend();++reiter){
	        	int num = 0; 
				if(reiter == digits.rbegin())
	        		num = *reiter + 1;
	        	else        		
	        	    num = *reiter;
				if(flag == 1)
	        		num = num +1;
	        	
	        	if(num > 9){
	        		num  = 0;
	        		flag = 1;
	        	}else{
	        		flag = 0;
	        	}
	        	temp_digits.push_back(num);
	        }
	        if(flag == 1)
	        	temp_digits.push_back(1);
	        
			for(reiter=temp_digits.rbegin();reiter<temp_digits.rend();++reiter){
				new_digits.push_back(*reiter);
			}
	        return new_digits;
	    }
	};
	// The codes below are used for test
	int main(){
		Solution s;
		vector<int> digits;
		digits.push_back(1);
		digits.push_back(2);	
		digits.push_back(9);
		vector<int> new_digits = s.plusOne(digits);
		vector<int>::iterator iter= new_digits.begin();
		for(;iter<new_digits.end();++iter){
			cout<<*iter<<endl;
		}
		system("pause");
		return 0;
	}


# Note
To solve the proble, I traverse the vector from end to begin and plus one to the element at end. If the element is larger than 10, we need a carry to the next element. Finally, we should reverse the vector.   
