# ds-algo-pilot
# 315. Count of Smaller Numbers After Self
Brute force solution :
class Solution {
    public List<Integer> countSmaller(int[] nums) {
        List<Integer> res=new ArrayList<>();
        for (int i=0;i<nums.length;i++){
            int count=0;
            for(int j=i+1;j<nums.length;j++){
                if(nums[i]>nums[j]){
                    count++;
                }
            }
            res.add(count);
        }
        return res;
    }
}


# https://leetcode.com/problems/first-missing-positive/description/
step 1: convert negative number of an array to with n+1;
step 2: mark the index whether its available or not

 public int firstMissingPositive(int[] nums) {
        
        int n=nums.length;
        for(int i=0;i<nums.length;i++){
            if(nums[i]<=0){
                nums[i]=n+1;
            }
        }
        for(int i=0;i<n;i++){
            int k=Math.abs(nums[i])-1;
            if(k < n && nums[k] > 0) {
            
                nums[k]*=(-1);
            }
        }
        for(int i=0;i<n;i++){
            if(nums[i]>0)
                return i+1;
        }
        return n+1;
    }
