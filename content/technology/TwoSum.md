---
title: "Two sum"
date: 2019-05-01T16:57:08+08:00
description: ""
type: ["blog","tech"]
tags: ["leetcode"]
comments: true
---


Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

<!--more-->

Example:
```java
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,

return [0, 1].

      class Solution {
      public int[] twoSum(int[] nums, int target) {
          if(nums == null || nums.length < 2){
              return new int []{-1,-1};
          }
          int[] result = new int[]{-1,-1};
          HashMap<Integer,Integer> map = new HashMap<>();
          for(int i = 0;i < nums.length;i++){
              if(map.containsKey(target-nums[i])){
                  result[0] = map.get(target-nums[i]);
                  result[1] = i; 
                  break;
              }
              map.put(nums[i],i);
          }
          return result;
      }
    } 
```
Solution 2:

```java
      class Solution {
      public int[] twoSum(int[] nums, int target) {
          HashMap<Integer, Integer> m = new HashMap<Integer, Integer>();
          int[] res = new int[2];
          for (int i = 0; i < nums.length; ++i) {
              m.put(nums[i], i);
          }
          for (int i = 0; i < nums.length; ++i) {
              int t = target - nums[i];
              if (m.containsKey(t) && m.get(t) != i) {
                  res[0] = i;
                  res[1] = m.get(t);
                  break;
              }
          }
          return res;
      }
      } 
```

两个代码有一点细节不同，第一个简化了两个for循环合并成一个，第二个对于新手来说更好理解。整个实现步骤为：先遍历一遍数组，建立HashMap映射，然后再遍历一遍，开始查找，找到则记录index


