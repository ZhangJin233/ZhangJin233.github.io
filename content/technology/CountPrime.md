---
title: "Count Prime"
date: 2019-04-16T16:57:08+08:00
description: ""
type: ["blog","tech"]
tags: ["leetcode"]
gitment: true
---


Count the number of prime numbers less than a non-negative number, n.

Example:

Input: 10

Output: 4

Explanation: There are 4 prime numbers less than 10, they are 2, 3, 5, 7.

solution 1:
```java
class Solution {
    public int countPrimes(int n) {
        boolean[] prime = new boolean[n];
        Arrays.fill(prime, true);
        for(int i = 2; i < n; i++){
            if(prime[i]){
                // 将i的2倍、3倍、4倍...都标记为非素数
                for(int j = i * 2; j < n; j =  j + i){
                    prime[j] = false;
                }
            }
        }
        int count = 0;
        for(int i = 2; i < n; i++){
            if(prime[i]) count++;
        }
        return count;
    }
}
```