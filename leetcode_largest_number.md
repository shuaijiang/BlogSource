title: Leetcode: Largest Number 
date: 2015-03-29 18:34:55
tags: leetcode
---

#Description
Given a list of non negative integers, arrange them such that they form the largest number.

For example, given [3, 30, 34, 5, 9], the largest formed number is 9534330.

Note: The result may be very large, so you need to return a string instead of an integer.

The original problem is [here](https://leetcode.com/problems/largest-number/ "here"):  
<!--more-->

#My Solution
I solve this problem in C++, as below:

	#include<iostream>
	#include<vector>
	#include<algorithm>
	#include<sstream>
	#include<math.h>
	#include<stdlib.h>
	
	using namespace std;
	
	class Solution {
	public:
	    string largestNumber(vector<int> &num) {
	        vector<int>::iterator iter,iterI,iterJ;
			int temp;
			stringstream ss;
			string str; 
			bool first_num = true;
			for(iterI=num.end()-1;iterI>=num.begin()+1;iterI--)
			{
				iterJ=iterI-1;
				do
				{
					if(largerNumber(*iterI,*iterJ))
					{
						temp = *iterJ;
						*iterJ = *iterI;
						*iterI = temp;
					}
					iterJ--;
				}while(iterJ>=num.begin());
			}
			for(iter=num.begin();iter<num.end();++iter)
			{
				if(first_num == true && *iter == 0)
				{
					ss<<*iter;
					break;
				}else
				{
					ss<<*iter;
					first_num = false;
				}
	
			} 
			str=(ss.str());
			return str;
	    }
	    vector<int> number2vector(int num){
			vector<int> vec;
			int remainder;
			if(num >0){
		        while(num>0){
					remainder = num%10;
					num = num/10;
					vec.push_back(remainder);
		        }
				reverse(vec.begin(),vec.end());
			}else{
				vec.push_back(num);
			}
			return vec;
	    }
		void vectorRaise(vector<int> & vec,int addSize)
		{
			vector<int>::iterator iter;
			
			for(int count=0;count<addSize;count++)
			{
				iter = vec.begin();
				//cout<<"iter="<<*iter<<endl;
				vec.push_back(*iter);
			}
				
		}
	    bool largerNumber(int a, int b){
			vector<int> vecA = number2vector(a);
			vector<int> vecB = number2vector(b);
			double ab = (double)a*pow(10,vecB.size()) + b;
			double ba = (double)b*pow(10,vecA.size()) + a;
			if(ab>ba)
				return true;
			else
				return false;
	 		/*vector<int>::iterator iterA;
			vector<int>::iterator iterB;
			if(vecA.size() > vecB.size())
			{
				int num = vecA.size()-vecB.size();
				vectorRaise(vecB,num);
			}
			else{
				int num = vecB.size()-vecA.size();
				vectorRaise(vecA,num);
			}
			for(iterA=vecA.begin(),iterB=vecB.begin();iterA<vecA.end()&&iterB<vecB.end();++iterA,++iterB)
			{
				if(*iterA > *iterB)
					return true;
				else if(*iterA < *iterB)
					return false;
			}
			if(vecA.size() > vecB.size())
				return false;
			else
				return true;
			*/
	    }
	};
	//The code below is used for test
	int main()
	{
		//int a[] = {3, 30, 34, 5, 9};
		//int a[] = {1440,7548,4240,6616,733,4712,883,8,9576};
		int a[] = {121,12};
		int arrayNum = 2;
	    Solution s;
		vector<int> vec;
	
		int numA = 8;
		int numB = 883;
		for(int count=0;count<arrayNum;count++)
			vec.push_back(a[count]);
		
		
		//vector<int>::iterator iter;
		string str = s.largestNumber(vec);
		cout<<"largest number is "<<str<<endl;
		bool larger = s.largerNumber(numA, numB);
		cout<<"larger="<<larger<<endl;
		system("pause");
		return 0;
		
	}


#Note
To find the largest number, we just sort the numbers according to descending order and then join them together. But one important thing need to be noted is how to select the larger number of any two numbers. We can't compare the two numbers as usual,  os we need to compare them after join them together at different order.