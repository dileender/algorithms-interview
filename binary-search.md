+ [Binary Search](#binary-search)

## Binary Search

https://leetcode.com/problems/binary-search/

```cpp
 int search(vector<int>& nums, int target) {
        if(nums.size() == 0)
            return -1;
        int low = 0;
        int high = nums.size() - 1;
        
        while(low <= high) {
            int middle = low + (high - low)/2;
            if(nums[middle] == target)
                return middle;
            else if(nums[middle] < target) {
                low = middle + 1;
            }
            else {
                high = middle - 1; 
            }
        }
        return -1;
    }
```
