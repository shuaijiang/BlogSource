title: LeetCode Rectangle Area
date: 2015-07-26 23:20:10
tags: leetcode
---


# Description
Find the total area covered by two rectilinear rectangles in a 2D plane.

Each rectangle is defined by its bottom left corner and top right corner as shown in the figure.

The original problem is [here](https://leetcode.com/problems/rectangle-area/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/RectangleArea.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*Rectangle Area
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<math.h>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
	    int computeArea(int A, int B, int C, int D, int E, int F, int G, int H) {
			double area1 = (C-A) * (D-B);
			double area2 = (G-E) * (H-F);
	
			double area3 = max(min((double)C,(double)G) - max((double)A,(double)E),0.0) * max(min((double)D,(double)H)-max((double)B,(double)F),0.0);
			
			double area = area1 + area2 - area3;
			
			return (int)area;
	    }
	};
	int main(){
		Solution s;
		int result = s.computeArea(-1500000001, 0, -1500000000, 1, 1500000000, 0, 1500000001, 1);
		cout<<"result="<<result<<endl;
		system("pause");
		return 0;
	}

# Note
To solve the problem, we need compute the areas of rectangles and then minus the area of the intersection part. 
