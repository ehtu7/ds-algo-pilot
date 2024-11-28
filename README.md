# ds-algo-pilot
# 315. Count of Smaller Numbers After Self
## Brute force solution :
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

## Optimal One : using sorting and binary search
Step1: create a list and sort it
step2: using binary search on sorted list find the index of each element
step3: add index to result and remove that indexed element from sorted list.
  public List<Integer> countSmaller(int[] nums) {
         //int[] arr = Arrays.copyOf(nums, nums.length); // Make a copy of the input array
         ArrayList<Integer> arr=new ArrayList<>();
         for(int i=0;i<nums.length;i++){
            arr.add(nums[i]);
         }

        Collections.sort(arr); // Sort the copied array

        List<Integer> res = new ArrayList<>();

        for(int i = 0; i<nums.length; i++){
            int index = binarySearch(arr,nums[i]);
            res.add(index);
            arr.remove(index);
        }
        return res;
    }
    public int binarySearch(ArrayList<Integer> list, int num){

        int s=0;
        int e=list.size()-1;
        int mid=0;
        while(s<=e){
            mid=s+((e-s)/2);
            if(list.get(mid)<num){
                s=mid+1;
            }else{
                e=mid-1;
            }

        }
        if(list.get(s)==num) return s;
        return mid;
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
