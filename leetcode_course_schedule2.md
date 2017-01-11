title: LeetCode Course Schedule2
date: 2015-10-09 15:46:14
tags: leetcode
---

# Description
There are a total of n courses you have to take, labeled from 0 to n - 1.

Some courses may have prerequisites, for example to take course 0 you have to first take course 1, which is expressed as a pair: [0,1]

Given the total number of courses and a list of prerequisite pairs, return the ordering of courses you should take to finish all courses.

There may be multiple correct orders, you just need to return one of them. If it is impossible to finish all courses, return an empty array.

For example:

	2, [[1,0]]
There are a total of 2 courses to take. To take course 1 you should have finished course 0. So the correct course order is [0,1]

	4, [[1,0],[2,0],[3,1],[3,2]]
There are a total of 4 courses to take. To take course 3 you should have finished both courses 1 and 2. Both courses 1 and 2 should be taken after you finished course 0. So one correct course order is [0,1,2,3]. Another correct ordering is[0,2,1,3].

The original problem is [here](https://leetcode.com/problems/course-schedule-ii/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/CourseSchedule2.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:
	
	/*
	*Course Schedule II 
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<queue>
	#include<vector>
	#include<stdlib.h>
	using namespace std;
	
	class Solution {
	public:
		queue<int> q;  //save the course whos prerequisites are all finished
		vector<int> res;
		vector<int> empty;
		vector<int> findOrder(int numCourses, vector<pair<int, int>>& prerequisites) {
	        if(numCourses <= 0 ){ //|| !canFinish(numCourses, prerequisites
	        	return res;
	        }
	        int len = prerequisites.size();
	        if(len == 0){
	        	for(int i=0;i<numCourses;i++)
	        		res.push_back(i);
	        	return res;
	        }
	        vector<int> preNum(numCourses, 0);
	        for(int i=0;i<len;i++){
	        	preNum[prerequisites[i].first] ++;
	        }
	        for(int i=0;i<numCourses;i++){
	        	if(preNum[i] == 0)
	        		q.push(i);
	        }
	        while(!q.empty()){
	        	int oneCourse = q.front();
	        	res.push_back(oneCourse);
	        	q.pop();
	        	for(int i=0;i<len;i++){
	        		int course = prerequisites[i].first;
	        		if(preNum[course] == 0)
	        			continue;
	        		if(prerequisites[i].second == oneCourse){
	        			preNum[course] --;
	        			if(preNum[course] == 0){
	        				q.push(course);
	        			}
	        		}
	        	}
	        }
	        if(res.size() != numCourses)
	        	return empty;
	        return res;
	    }
	
	};
	
	int main(){
		Solution s;
		pair<int, int> n1(0,1);
		//pair<int, int> n2(2,0);
		//pair<int, int> n3(3,1);
		//pair<int, int> n4(3,2);
		
		vector<pair<int,int> > vec;
		vec.push_back(n1);
		//vec.push_back(n2);
		//vec.push_back(n3);
		//vec.push_back(n4);
		vector<int> res = s.findOrder(2, vec);
		for(int i=0;i<res.size();i++)
			cout<<res[i]<<endl;
		system("pause");
		return 0;
	}

# Note
借鉴了广度优先搜索遍历的思想。首先，得到不需要依赖其他课程的课程C0（肯定存在，否则无法完成整个课程安排）；其次，遍历C0，将所有依赖这些课程C0的课程C1的依赖课程数目减一，如果减为零，则该课程也退化为不需要依赖其他课程的课程， 将该课程加入到C0。在遍历C0的过程，即是得到结果的过程。
