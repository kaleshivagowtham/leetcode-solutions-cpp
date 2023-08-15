#**53. Maximum Subarray**
------------------------------------

##**Approach**
------------------------
Take 2 pointers i and j. Find the sum only betewwn i and j at each iteration, and if the sum is grater than the previousmaximum sum, update the maximum sum. Else if the sum is < 0,iterate the i to a location where the negative sum will be removed(i.e. i=j+1).

##**Complexity**
------------------------
Time complexity:O(n)
Space complexity:O(1)

##**Code**
------------------------
```
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        
        int sum=0,maxSum=INT_MIN,n=nums.size(),i=0,j=0;
        while(i<=j && j<n) {
            sum += nums[j];
            maxSum = max(maxSum , sum);
            if(sum < 0){
                i=j+1;
                sum=0;
            }
            j++;
        }
        return maxSum;
    }
};
```