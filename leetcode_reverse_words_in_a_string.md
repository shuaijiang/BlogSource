title: LeetCode Reverse Words in a String 
date: 2015-06-26 15:43:49
tags: leetcode
---



# Description
Given an input string, reverse the string word by word.

For example,
Given s = "the sky is blue",
return "blue is sky the".

The original problem is [here](https://leetcode.com/problems/reverse-words-in-a-string/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/ReverseWordsInAString.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	

	/*
	*Reverse Words in a String
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    void reverseWords(string &s) {
			s = filter(s);
	    	if(s.length()<=0)
	    		return;
	    	
	    	//cout<<"s="<<s<<endl;
	        string substr, newstr;
	        int begin,end,sublen;
	        end = s.length() - 1;
	        for(int i=s.length()-1;i>=0;i--){
	        	if(s[i] == ' '){
	        		begin = i+1;
	        		sublen = end - begin + 1;
	        		end = i - 1;
	        		substr=s.substr(begin,sublen);
	        		strcat(newstr,substr);
	        	}
	        }
	        substr=s.substr(0,end+1);
	        strcat(newstr,substr);
	        s = newstr;
	    }
	    void strcat(string &s, string str){
	    	if(s.length() > 0){
	    		s.push_back(' ');
	    	}
	    	for(int i=0;i<str.length();++i){
	    		s.push_back(str[i]);
	    	}
	    }
	    //Remove the space at the begining, middle or end of the string
	    string filter(string s){
	    	string str;
	    	int begin = 0, end=s.length()-1;
	    	while(begin < s.length() && s[begin] == ' '){
	    		begin ++;
	    	}
	    	while(end >=0 && s[end] == ' '){
	    		end --;
	    	}
	    	for(int count=begin;count<=end;count++){
	    		if(s[count]!= ' ')
	    			str.push_back(s[count]);
				else if(s[count+1] != ' ')
					str.push_back(s[count]);
	    	}
	    	return str;
	    }
	};
	//The code under below is used for test
	int main(){
		string str(" We are   friends ");
		Solution s;
		s.reverseWords(str);
		cout<<"new str="<<str<<endl;
		system("pause");
		return 0;
	}


# Note
In the solution, first, we remove the space in the begining and end of the string, and the multiple spaces between two words. Then, we traverse the string from end to the begining, if we get a space, we know that it is separator of a word. Put all the words in a new string with space as the separator. Finally, we get the string with the reverse words. 
