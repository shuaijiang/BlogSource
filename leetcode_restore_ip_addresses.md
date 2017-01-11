title: LeetCode Restore IP Addresses
date: 2015-10-20 19:29:25
tags: leetcode
---


# Description
Given a string containing only digits, restore it by returning all possible valid IP address combinations.

For example:
Given "25525511135",

return ["255.255.11.135", "255.255.111.35"]. (Order does not matter)

The original problem is [here](https://leetcode.com/problems/restore-ip-addresses/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/RestoreIPAddresses.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Restore IP Addresses
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<vector>
	#include<sstream>
	using namespace std;
	
	class Solution {
	public:
		vector<string> res;
	    vector<string> restoreIpAddresses(string s) {
	        string str;
	        dfs(s, str, 0);
	        return res;
	    }
	    bool dfs(string s, string str, int level){
	    	stringstream ss;
	    	int num;
			
			if(level == 3){
				ss<<s;
		    	ss>>num;
		    	ss.clear();
		    	
		    	if(s[0] == '0' && s.size()>1) //if one part has more than 1 integer, the begining can't be 0 
		    		return false;
				if(num <= 255){
					str.push_back('.');
					str+=s;
					res.push_back(str);
					return true;
				}
				return false;
			}
			string substr;
			string remain;
			for(int i=0;i<3 && i<s.size();++i){
				substr = s.substr(0,i+1);
				if(substr[0] == '0' && substr.size() > 1)
					continue;
				ss<<substr;
				ss>>num;
				ss.clear();
				if(num <= 255){
					if(str.size()>0) // if first part should not add '.'
						str.push_back('.');
					str += substr;
					remain = s.substr(i+1, s.size()-i-1);
					
					if(remain.size() >= 3-level)
						dfs(remain, str, level+1);
					
					if(str == substr)
						str = "";
					else
						str = str.substr(0, str.size() - substr.size() - 1);
				}
				else{
					return false;
				}
			}
	    }
	};
	
	int main(){
		Solution s;
		//string str("25525511135");
		string str("010010");
		vector<string> res = s.restoreIpAddresses(str);
		for(int i=0;i<res.size();++i){
			cout<<res[i]<<endl;
		}
		return 0;
	}


# Note
因为对一个给定的字符串，存在多种可能得IP地址，考虑采用深度优先遍历方法，找出所有合法的IP地址。需要注意的是，每个字段如果超过2位，则第一位不可以是0。
