title: LeeCcode： LRU Cache
date: 2015-08-13 21:37:50
tags: leetcode
---

# Description
Design and implement a data structure for Least Recently Used (LRU) cache. It should support the following operations: get and set.

get(key) - Get the value (will always be positive) of the key if the key exists in the cache, otherwise return -1.
set(key, value) - Set or insert the value if the key is not already present. When the cache reached its capacity, it should invalidate the least recently used item before inserting a new item.

The original problem is [here](https://leetcode.com/problems/lru-cache/ "Problem").

The original code is [here](https://github.com/shuaijiang/LeetCode/blob/master/LRUCache.cpp "Code").
<!--more-->

# My Solution
I solve this problem in C++, as below:

	/*
	*LRU Cache
	*Author: shuaijiang
	*Email: zhaoshuaijiang8@gmail.com
	*/
	#include<iostream>
	#include<stack>
	#include<stdlib.h>
	using namespace std;
	
	class LRUCache{
	public:
	    LRUCache(int capacity) {
	        this->capacity = capacity;
	    }
	    
	    int get(int key) {
	        if(cacheMap.find(key) == cacheMap.end())
	        	return -1;
	        
	        cacheList.splice(cacheList.begin(), cacheList, cacheMap[key]);
	        cacheMap[key] = cacheList.begin();
	        return cacheMap[key]->value;
	    }
	    
	    void set(int key, int value) {
	        if(cacheMap.find(key) == cacheMap.end()){
	        	if(capacity == cacheList.size()){
	        		cacheMap.erase(cacheList.back().key);
	        		cacheList.pop_back(); 
	        	}
	        	CacheNode node(key,value);
	        	cacheList.push_front(node);
	        	cacheMap[key] = cacheList.begin();
	        }
	        else{
	        	cacheList.splice(cacheList.begin(), cacheList, cacheMap[key]);
	        	cacheMap[key] = cacheList.begin();
	        	cacheMap[key]->value = value;
	        }
	        
	    }
	private:
		struct CacheNode{
			int key;
			int value;
			CacheNode(int k, int v):key(k), value(v){}
		};
		int capacity;
		list<CacheNode> cacheList;
		map<int, list<CacheNode>::iterator> cacheMap;
	};

# Note
To solve the problem, a bidirector list and a hashmap are needed. For every operation, put the visited node to the head of the list.  
