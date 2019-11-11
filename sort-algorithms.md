+ [Sort an Array](#sort-an-array)

## Sort an Array

https://leetcode.com/problems/sort-an-array/

QuickSort
```cpp
vector<int> sortArray(vector<int>& nums) {
  int left = 0, right = nums.size() - 1;
  quickSort(nums, left, right);
  return nums;
}

void quickSort(vector<int>& A, int left, int right) {
  if (left >= right) return;
  int pi = A[left];
  while (left < right) {
    while (A[right] > pi && left < right) right--;
    if (left < right) {
      A[left] = A[right];
      left++;
    }
    while (A[left] < pi && left < right) left++;
    if (left < right) {
      A[right] = A[left];
      right--;
    }
  }
  A[left] = pi;
  int pi_i = left;
  quickSort(A, left, pi_i - 1);
  quickSort(A, pi_i + 1, right);
}
```
