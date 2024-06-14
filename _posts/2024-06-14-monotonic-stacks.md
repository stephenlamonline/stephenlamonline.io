---
layout: post
title: Monotonic Stacks
date: 2024-06-14 23:05
description: tutorial of Monotonic Stacks and some related problems
tags: ICPC training
categories: sample-posts
---

# Monotonic stacks

## Introduction 
- monotonic stack is a data structure that stores elements in either a increasing or decreasing order. It is essentially still a stack, with an additional sort of ordering.

## Monotonic increasing stack

### Implementation
``` cpp
void printincreasing(int n, vector<int> arr){
    stack<int> s;
    vector<int> ans;
    s.push(arr[0]); 

    for(int i=1; i<n; i++){
        while(!s.empty() && s.top()>arr[i]){
            s.pop();
        }
        s.push(arr[i]);
    }

    while (!s.empty())
    {
        ans.push_back(s.top());
        s.pop();
    }
    for(int i = ans.size()-1; i>=0; i--){
        cout<<ans[i]<<" ";
    }
}
```

### Example Question : Next Greater Element I
> https://leetcode.com/problems/next-greater-element-i/

```cpp
class Solution {
public:
    vector<int> nextGreaterElement(vector<int>& nums1, vector<int>& nums2) {
        vector<int>output;
        for(int i : nums1){
            bool flag = false, f2 = false;
            for(int k=0; k<nums2.size();k++){
                if(i == nums2[k] || flag == true){
                    flag = true;
                    if(nums2[k]>i){
                        f2 = true;
                        output.push_back(nums2[k]);  
                        break;
                    }                                       
                }
            }
            if(!f2)
                output.push_back(-1);
        }
        return output;
    }
};
```
## Monotonic decreasing stack
> to be continued