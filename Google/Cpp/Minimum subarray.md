**描述**
==
Given an array of integers, find the subarray with smallest sum.

Return the sum of the subarray.

例如：
For [1, -1, -2, 1], return -3.
收集数组最小和

**代码**
==
        class Solution {
        public:
            /*
             * @param nums: a list of integers
             * @return: A integer indicate the sum of minimum subarray
             */
            int minSubArray(vector<int> &nums) {
                // write your code here
                int minarray = nums[0];
                int sum = 0 ;
                int maxarray = 0;
                for(int i = 0; i<nums.size(); i++){
                    sum += nums[i];
                    if(sum - maxarray < minarray){
                        minarray = sum - maxarray;
                    }
                    if(sum > maxarray)
                        maxarray = sum;
                }
                return minarray;
            }
        };
