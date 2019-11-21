+ [Path Sum](#path-sum)
+ [Path Sum II](#path-sum-ii)
+ [Maximum Depth of Binary Tree](#maximum-depth-of-binary-tree)

## Path Sum

https://leetcode.com/problems/path-sum/

```cpp
bool hasPathSum(TreeNode* root, int sum) {
  if (root == nullptr) return false;

  if (root->left == nullptr && root->right == nullptr && root->val == sum)
    return true;

  return (hasPathSum(root->left, sum - root->val) ||
          hasPathSum(root->right, sum - root->val));
}
```

## Path Sum II

https://leetcode.com/problems/path-sum-ii/

```cpp
vector<vector<int>> pathSum(TreeNode* root, int sum) {
  vector<vector<int>> res;
  if (root == nullptr) return res;
  vector<int> temp;
  CreatePahtSum(root, sum, temp, res);
  return res;
}
void CreatePahtSum(TreeNode* root, int sum, vector<int> temp,
                   vector<vector<int>>& res) {
  if (!root) return;
  temp.push_back(root->val);
  if (sum - root->val == 0 && root->left == nullptr && root->right == nullptr) {
    res.push_back(temp);
    return;
  }
  CreatePahtSum(root->left, sum - root->val, temp, res);
  CreatePahtSum(root->right, sum - root->val, temp, res);
}
```

## Maximum Depth of Binary Tree

https://leetcode.com/problems/maximum-depth-of-binary-tree/

```cpp
int maxDepth(TreeNode* root) {
  if (root == NULL) return 0;

  int res = 0;
  queue<TreeNode*> q;
  q.push(root);
  while (!q.empty()) {
    ++res;
    for (int i = 0, n = q.size(); i < n; ++i) {
      TreeNode* p = q.front();
      q.pop();

      if (p->left != NULL) {
        q.push(p->left)
      };
      if (p->right != NULL) {
        q.push(p->right)
      };
    }
  }

  return res;
}
```
