title: LeetCode Gas Station
date: 2015-06-27 09:10:19
tags: leetcode
---


# Description
There are N gas stations along a circular route, where the amount of gas at station i is gas[i].

You have a car with an unlimited gas tank and it costs cost[i] of gas to travel from station i to its next station (i+1). You begin the journey with an empty tank at one of the gas stations.

Return the starting gas station's index if you can travel around the circuit once, otherwise return -1.


The original problem is [here](https://leetcode.com/problems/gas-station/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/GasStation.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*
	*Gas Station 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stdlib.h>
	using namespace std;
	public:
	    int canCompleteCircuit(vector<int>& gas, vector<int>& cost) {
	    	int i = 0, j = 0; 
	        while(i<gas.size()){
	        	j = i;
	        	if(isCircuit(gas,cost,&j)){
	        		return i;
	        	}
				else if(i==j){
					i++;        		
	        	}
	        	else
	        		i = j;
	        }
	        return -1;
	    }
	    bool isCircuit(vector<int>& gas, vector<int>& cost,int *i){
	    	int gasLeft = 0;
	    	int count = *i;
	    	do{
	    		gasLeft += gas[count] -cost[count];
	    		if(gasLeft < 0){
	    			*i = count+1;
	    			return false;
	    		}
	    		count ++;
	    		if(count == gas.size())
	    			count = 0;
	    	}while(count != *i);
	    	
	    	return true;
	    }
	};
	
	
	//Method2: Time Limit Exceeded
	class Solution {
	public:
	    int canCompleteCircuit(vector<int>& gas, vector<int>& cost) {
	        for(int i=0;i<gas.size();++i){
	        	if(isCircuit(gas,cost,i))
	        		return i;
	        }
	        return -1;
	    }
	    bool isCircuit(vector<int>& gas, vector<int>& cost,int i){
	    	int gasLeft = 0;
	    	int count = i;
	    	do{
	    		gasLeft += gas[count] -cost[count];
	    		if(gasLeft < 0)
	    			return false;
	    		count ++;
	    		if(count == gas.size())
	    			count = 0;
	    	}while(count != i);
	    	return true;
	    }
	};

# Note
In the solution, the basic idea which tests every station as the begining is expand the time.  A good idea is that if start from i and end at j, because at j the gas is unenough, then we restart from j+1, and test wheather j+1 is right. 
