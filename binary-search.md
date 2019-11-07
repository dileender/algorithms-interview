+ [Binary Search](#binary-search)
+ [Search in Rotated Sorted Array](#search-in-rotated-sorted-array)
+ [Find Minimum in Rotated Sorted Array](#find-minimum-in-rotated-sorted-array)
+ [Find K Closest Elements](#find-k-closest-elements)

## Binary Search

https://leetcode.com/problems/binary-search/

```cpp
int search(vector<int>& nums, int target) {
  if (nums.size() == 0) return -1;
  int low = 0;
  int high = nums.size() - 1;

  while (low <= high) {
    int middle = low + (high - low) / 2;
    if (nums[middle] == target) {
      return middle;
      }
    else if (nums[middle] < target) {
      low = middle + 1;
    } else {
      high = middle - 1;
    }
  }
  return -1;
}
```

## Search in Rotated Sorted Array

https://leetcode.com/problems/search-in-rotated-sorted-array/

```cpp
int search(vector<int>& nums, int target) {
  int left = 0, right = nums.size() - 1;
  while (left <= right) {
    int middle = (right - left) / 2 + left;
    if (nums[middle] == target) { 
       return middle;
       }
    if (nums[middle] < nums[right]) {
      if (nums[middle] < target && target <= nums[right]) {
        left = middle + 1;
      } else {
        right = middle - 1;
      }
    } else {
      if (nums[left] <= target && target < nums[middle]) {
        right = middle - 1;
      } else {
        left = middle + 1;
      }
    }
  }
  return -1;
}
```

## Find Minimum in Rotated Sorted Array

https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/

```cpp
int findMin(vector<int>& nums) {
  int left = 0, right = nums.size() - 1;
  while (left < right && nums[left] > nums[right]) {
    int mid = left + (right - left) / 2;
    if (nums[mid] > nums[right]) {
      left = mid + 1;
    } else {
      right = mid;
    }
  }
  return nums[left];
}
```

## Find K Closest Elements

https://leetcode.com/problems/find-k-closest-elements/

```cpp
vector<int> findClosestElements(vector<int>& arr, int k, int x) {
  int left = 0, right = arr.size() - k;
  while (left < right) {
    int mid = (left + right) / 2;
    if ((x - arr[mid]) > (arr[mid + k] - x)) {
      left = mid + 1;
    } else {
      right = mid;
    }
  }
  return vector<int>(arr.begin() + left, arr.begin() + left + k);
}
```
