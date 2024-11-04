# 704. Binary Search
## **Solution** 
The Binary Search is the best way to solve the problem because the time cpmplexity will be O(logn). Using two index _"left"_ and _"right"_ as the start and end of the array. The key idea is to calculate the middle index, compare the _nums[mid]_ with the target, and adjust _"left"_ and _"right"_ based on whether the target is greater or smaller than the _nums[mid]_.

## **Code**
```
public int search(int[] nums, int target){

  int left = 0;
  int right = nums.length - 1;

  while(left <= right){
    int mid = left + (right - left) / 2;
    if(nums[mid] == target) return mid;
    else if (nums[mid] < target) left = mid + 1;
    else right = mid - 1;
  }

  return -1;
}
```
--------
# 27. Remove Element
## **Solution**

