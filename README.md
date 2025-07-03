# DSA
Q1.Maximum subarray sum
class Solution {
    public int maxSubArray(int[] nums) {
        int maxsum=nums[0];
        int currentsum=nums[0];
        for(int i=1;i<nums.length;i++)
        {
            currentsum=Math.max(nums[i],currentsum+nums[i]);
            maxsum=Math.max(currentsum,maxsum);
        }
        return maxsum;
    }
}

Q2.Maximun subarray product
class Solution {
    public int maxProduct(int[] nums) {
        int currMax = nums[0];
        int currMin = nums[0];
        int result = nums[0];

        for (int i = 1; i < nums.length; i++) {
            int tempMax = Math.max(nums[i], Math.max(currMax * nums[i], currMin * nums[i]));
            currMin = Math.min(nums[i], Math.min(currMax * nums[i], currMin * nums[i]));
            currMax = tempMax;

            result = Math.max(result, currMax);
        }

        return result;
    }
}

Q3.the total number of subarrays whose sum equals to k.

class Solution {
    public int subarraySum(int[] nums, int k) {
        int count = 0;
        int n = nums.length;

        // Try every starting index i
        for (int i = 0; i < n; i++) {
            int sum = 0;

            // Extend the subarray to the right from i to j
            for (int j = i; j < n; j++) {
                sum += nums[j];

                if (sum == k) {
                    count++;
                }
            }
        }

        return count;
    }
}

