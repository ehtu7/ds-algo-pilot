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
