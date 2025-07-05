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

Q4.Majority Element

class Solution{
public int majorityElement(int nums[])
{
int c=0;
int c1=0;
for(int i=0;i<nums.length;i++)
{
int num=nums[i];
if(c==0)
c1=num;
c+=(num==c1)?1:-1;
}
return c1;
}
}



Q5. Best time to buy and sell stocks 2
class Solution {
    public int maxProfit(int[] prices) {
        int profit=0;
        for(int i=1;i<prices.length;i++)
        {
            if(prices[i]>prices[i-1])
            profit+=prices[i]-prices[i-1];
        }
        return profit;
    }
}



Q6.No. of zero filled subarrays
class Solution {
    public long zeroFilledSubarray(int[] nums) {
        long count = 0;
        long current = 0;

        for (int num : nums) {
            if (num == 0) {
                current++;
                count += current;  // add the number of subarrays ending here
            } else {
                current = 0; // reset
            }
        }

        return count;
    }
}
