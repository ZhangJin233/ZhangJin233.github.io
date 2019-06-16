---
title: "Happy Number"
date: 2019-05-02T16:57:08+08:00
description: ""
type: ["Blog","Technology"]
tags: ["leetcode"]
comments: true
---

## Happy Number

Write an algorithm to determine if a number is "happy".

A happy number is defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits in base-ten, and repeat the process until the number either equals 1 (where it will stay), or it loops endlessly in a cycle that does not include 1. Those numbers for which this process ends in 1 are happy numbers, while those that do not end in 1 are unhappy numbers (or sad numbers).

```java
    class Solution {
        public boolean isHappy(int n) {
            HashSet<Integer> hashset = new HashSet<Integer>();
            int m =n;
            hashset.add(m);
            while(true){
                m = squareSum(m);
                if(m == 1){
                    return true;
                }else if(hashset.contains(m)){
                    return false;
                }
                // why?
                hashset.add(m);
            }
        }
         private int squareSum(int n){
            int sum = 0;
            while(n != 0){
                sum += (n%10)*(n%10);
                n /= 10;
            }
            return sum;
        }
    }
```
  看到另一种解法：

```java
    //  Java program to check a number is a Happy 
    //  number or not 

    class GFG { 

    // Utility method to return sum of square of 
    // digit of n 
    static int numSquareSum(int n) 
    { 
        int squareSum = 0; 
        while (n!= 0) 
        { 
            squareSum += (n % 10) * (n % 10); 
            n /= 10; 
        } 
        return squareSum; 
    } 

    //  method return true if n is Happy number 
    static boolean isHappynumber(int n) 
    { 
        int slow, fast; 

        //  initialize slow and fast by n 
        slow = fast = n; 
        do
        { 
            //  move slow number 
            // by one iteration 
            slow = numSquareSum(slow); 

            //  move fast number 
            // by two iteration 
            fast = numSquareSum(numSquareSum(fast)); 

        } 
        while (slow != fast); 

        //  if both number meet at 1, 
        // then return true 
        return (slow == 1); 
    } 

    //  Driver code to test above methods 
    public static void main(String[] args) 
    { 
        int n = 13; 
        if (isHappynumber(n)) 
            System.out.println(n +  
            " is a Happy number"); 
        else
            System.out.println(n +  
            " is not a Happy number"); 
    } 
} 
```