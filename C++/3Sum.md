[![Travis](https://img.shields.io/badge/%E9%9A%BE%E5%BA%A6-%E4%B8%AD%E7%AD%89-orange)]()

## 题目地址

https://leetcode-cn.com/problems/3sum/

## 题目描述

```
给定一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0

找出所有满足条件且不重复的三元组。

注意：答案中不可以包含重复的三元组。


示例:

输入：nums = [-1, 0, 1, 2, -1, -4]

输出：
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```

## 思路

### 暴力法 (不可取)

借助Two-Sum思想，固定其中一个数，在剩下数组中寻找另外两个数

```c++
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> result;
        if(nums.size()<3)
            return result;
        sort(nums.begin(), nums.end());

        for(int i=0; i<nums.size()-2; i++){
            if((i>0)&&(nums[i] == nums[i-1]))
                continue;
            int target = -nums[i];
            vector<int> ans;
            
            // 考虑two sum
            for(int j=i+1; j<nums.size()-1; j++){
                if((nums[j] == nums[j-1]) && (j>i+1))
                    continue;
                int complement = target - nums[j];
                vector<int>::iterator another = find(nums.begin()+j+1, nums.end(), complement); 
                if(another != nums.end()){
                    ans.push_back(nums[i]);
                    ans.push_back(nums[j]);
                    ans.push_back(*another);
                    result.push_back(ans);
                    ans.clear();
                }
            }

        }
        return result;
    }
};
```
为了判断数组重复性，使用了排序，增加了O(nlogn)的时间复杂度

> 时间复杂度：O(n^3)

### 双指针

思想仍然是固定其中一个数，但利用双指针指向额外的数，借此求和并判断重复

```c++

```
