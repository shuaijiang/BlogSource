title: LeetCode Count Primes
date: 2015-10-20 17:25:09
tags: leetcode
---


# Description
Count the number of prime numbers less than a non-negative number, n.

The original problem is [here](https://leetcode.com/problems/count-primes/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/CountPrimes.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Count Primes 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<map>
	#include<sstream>
	#include<math.h>
	using namespace std;
	
	class Solution {
	public:
	    int countPrimes(int n) {
	        vector<bool> isPrime(n, true);
	        // Loop's ending condition is i * i < n instead of i < sqrt(n)
	        // to avoid repeatedly calling an expensive function sqrt().
	        for (int i = 2; i * i < n; i++) {
	          if (!isPrime[i]) continue;
	          for (int j = i * i; j < n; j += i) {
	             isPrime[j] = false;
	          }
	        }
	        int count = 0;
	        for (int i = 2; i < n; i++) {
	          if (isPrime[i]) count++;
	        }
	        return count;
	    }
	};

# Note
参考了[Sieve_of_Eratosthenes](https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes "维基百科")。
