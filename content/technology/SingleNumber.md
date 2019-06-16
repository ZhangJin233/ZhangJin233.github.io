---
title: "SingleNumber"
date: 2019-04-01T16:57:08+08:00
description: ""
type: ["blog","tech"]
tags: ["leetcode"]
comments: true
---

Given a non-empty array of integers, every element appears twice except for one. Find that single one.

Note:

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

Example 1:

Input: [2,2,1]

Output: 1

Example 2:

Input: [4,1,2,1,2]

Output: 4



solution 1:

hashmap

```java
    class Solution {
        public int singleNumber(int[] nums) {
            if(nums == null || nums.length == 0){
                return 0;
            }
            HashMap<Integer,Integer> map = new HashMap<Integer,Integer>();
            for(int i=0;i<nums.length;i++){
                if(!map.containsKey(nums[i])){
                    map.put(nums[i],1);
                }
                else{
                    map.remove(nums[i]);
                }
            }
            for(Map.Entry<Integer, Integer> m : map.entrySet()){
                return m.getKey();
            }
            return 0;
        }
    }
```



solution 2:

这里运用到异或的性质：对于任何数x，都有x^x=0，x^0=x

```java
    class Solution{
        public int singleNumber(int[] nums){
            for (int i = 1; i < nums.length; i++) {
             nums[i] = nums[i] ^ nums[i-1];
         }
         return nums[nums.length-1];
        }
    }
 

     class Solution{
        public int singleNumber(int[] nums){
            int num = nums[0];
            for (int i = 1; i < nums.length; i++) {
                num = num ^ nums[i];
            }   
            return num;
        }
    }

    class Solution{
        public int singleNumber(int[] nums){
            int num = 0;
            for (int i = 0; i < nums.length; i++) {
                num = num ^ nums[i];
            }   
            return num;
        }
    }
```