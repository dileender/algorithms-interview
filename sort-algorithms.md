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
MergeSort
```cpp
vector<int> sortArray(vector<int>& nums) {
  int l = 0, r = nums.size() - 1;
  vector<int> temp(r - l + 1);
  mergeSort(nums, temp, l, r);
  return nums;
}

void mergeSort(vector<int>& A, vector<int>& temp, int l, int r) {
  if (l >= r) return;
  int m = (l + r) / 2;
  mergeSort(A, temp, l, m);
  mergeSort(A, temp, m + 1, r);
  merge(A, temp, l, m, r);
}

void merge(vector<int>& A, vector<int>& temp, int l, int m, int r) {
  int p1 = l, p2 = m + 1, p_temp = 0;
  while (p1 <= m && p2 <= r) {
    if (A[p1] <= A[p2])
      temp[p_temp++] = A[p1++];
    else
      temp[p_temp++] = A[p2++];
  }
  while (p1 < m + 1) temp[p_temp++] = A[p1++];
  while (p2 < r + 1) temp[p_temp++] = A[p2++];
  for (int i = 0; i < r - l + 1; i++) {
    A[l + i] = temp[i];
  }
}
```
