# 209. Minimum Size Subarray Sum
## Solution
The Sliding Window effciently manage a window of contiguous elements that meet the target sum reuqirement. We start by initializing a pointer "left" at the start of the array, and then use a for loop to move a pointer "right" from the beginning to the end of the array. 
At each step, we add nums[right] to currentSum, expanding the window to include nums[right]. When the currentSum is greater than or equal to the target, we have found a valid subarray that fullfills requirement. We need to calculate the length of the subarray as "right - left + 1", if the length is smaller than the current minLength, updating the minLength with new value. Next we need to find if there is shorter window that meets the target, so we move "left" pointer one step to the right, which removes the nums[left] from currentSum, we repeat the shrinking process as long as the currentSum still equals oor exceeds the target, aiming to find a minimum possible window size. At the end of the loop, if minlength is updated from its initial value, we return it as the shortest valid subarray length, if minLength still as its initial value, it means no subarray meets the target, we return 0. 

## Code
```
//Brute Force
public int minSubArrayLen(int target, int[] nums) {

  int minLength = Integer.MAX_VALUE;

  for(int start = 0; start < nums.length; start++){
    int sum = 0;

    for(int end = start; end < nums.length; end++){
      sum += nums[end];
      if(sum >= target){
        minLength = Math.min(minLength, end - start + 1);
        break;
      }
    }
  }
  return minLength == Integer.MAX_VALUE ? 0 : minLength;
}
```

```
public int minSubArrayLen(int target, int[] nums) {
  int left = 0; 
  int currentSum = 0;
  int minLength = Integer.MAX_VALUE;
  for(int right = 0; right < nums.length; right++){
    currentSum += nums[right];
    while(currentSum >= target){
      minLength = Math.min(right - left + 1, minLength);
      currentSum -= nums[left];
      left++;
    }
  }
  return minLength == Integer.MAX_VALUE ? 0 : minLength;
}
```

----------
