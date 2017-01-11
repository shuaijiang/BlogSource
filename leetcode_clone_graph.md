title: LeetCode Clone Graph
date: 2015-08-13 17:58:35
tags: leetcode
---

# Description
Clone an undirected graph. Each node in the graph contains a label and a list of its neighbors.

The original problem is [here](https://leetcode.com/problems/clone-graph/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/CloneGraph.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

		/*
		*Clone Graph
		*Author: shuaijiang
		*Email: zhaoshuaijiang8@gmail.com
		*/
		
		#include<iostream>
		#include<vector>
		#include <unordered_set>
		#include<string.h>
		#include<stdlib.h>
		
		/**
		 * Definition for undirected graph.
		 * struct UndirectedGraphNode {
		 *     int label;
		 *     vector<UndirectedGraphNode *> neighbors;
		 *     UndirectedGraphNode(int x) : label(x) {};
		 * };
		 */
		class Solution {
		public:
		    UndirectedGraphNode *cloneGraph(UndirectedGraphNode *node) {
		        if(node == NULL)
		        	return NULL;
		        map<UndirectedGraphNode*, UndirectedGraphNode*> copied;
				clone(node, copied);
		       	return copied[node];
		    }
		    UndirectedGraphNode *clone(UndirectedGraphNode *node, map<UndirectedGraphNode*, UndirectedGraphNode*> copied) {
		        if(node == NULL)
		        	return NULL;
		        if(copied.find(node) != copied.end()) 
		        	return copied[node];
		        UndirectedGraphNode * root = new UndirectedGraphNode(node->label);
		       	vector<UndirectedGraphNode *> neighbors = node->neighbors;
		       	copied[node] = root;
		       	for(int i=0;i<neighbors.size(); i++){
		       		UndirectedGraphNode * temp = neighbors[i];
		       		UndirectedGraphNode * neighbor = cloneGraph(temp, copied);
		       		root->neighbors.push_back(neighbor);
		       	}
		       	return root;
		    }
		};

# Note
To solve the problem, depth-first search was used. In order to avoid the node to be copied more than once, a map was also need. 
