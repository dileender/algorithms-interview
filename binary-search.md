+ [Binary Search](#binary-search)
+ [Search in Rotated Sorted Array](#search-in-rotated-sorted-array)

## Binary Search

https://leetcode.com/problems/binary-search/

```cpp
int search(vector<int>& nums, int target)
{
    if (nums.size() == 0)
        return -1;
    int low = 0;
    int high = nums.size() - 1;

    while (low <= high) {
        int middle = low + (high - low) / 2;
        if (nums[middle] == target)
            return middle;
        else if (nums[middle] < target) {
            low = middle + 1;
        }
        else {
            high = middle - 1;
        }
    }
    return -1;
}
```

## Search in Rotated Sorted Array

https://leetcode.com/problems/search-in-rotated-sorted-array/

```cpp
int search(vector<int>& nums, int target)
{
    int left = 0, right = nums.size() - 1;
    while (left <= right) {
        int middle = (right - left) / 2 + left;
        if (nums[middle] == target)
            return middle;
        if (nums[middle] < nums[right]) {
            if (nums[middle] < target && target <= nums[right]) {
                left = middle + 1;
            }
            else {
                right = middle - 1;
            }
        }
        else {
            if (nums[left] <= target && target < nums[middle]) {
                right = middle - 1;
            }
            else {
                left = middle + 1;
            }
        }
    }
    return -1;
}
```