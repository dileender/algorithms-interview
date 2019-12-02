+ [Path Sum](#path-sum)
+ [Path Sum II](#path-sum-ii)
+ [Maximum Depth of Binary Tree](#maximum-depth-of-binary-tree)
+ [Maximum Depth of N-ary Tree](#maximum-depth-of-n-ary-tree)
+ [Binary Tree Inorder Traversal](#binary-tree-inorder-traversal)
+ [Binary Tree Level Order Traversal](#binary-tree-level-order-traversal)
+ [Symmetric Tree](#symmetric-tree)
+ [Same Tree](#same-tree)

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

## Maximum Depth of N-ary Tree

https://leetcode.com/problems/maximum-depth-of-n-ary-tree/

```cpp
int maxDepth(Node* root) {
  int depth = 0;

  if (root == nullptr) {
    return 0;
  }

  queue<Node*> q;
  q.push(root);

  while (!q.empty()) {
    int siz = q.size();
    while (siz--) {
      Node* n = q.front();
      q.pop();

      for (int i = 0; i < (n->children.size()); i++) {
        q.push(n->children[i]);
      }
    }

    depth++;
  }

  return depth;
}
```

## Binary Tree Inorder Traversal

https://leetcode.com/problems/binary-tree-inorder-traversal/

```cpp
vector<int> inorderTraversal(TreeNode* root) {
  vector<int> res;
  inorder(root, res);
  return res;
}
void inorder(TreeNode* root, vector<int>& res) {
  if (!root) {
    return;
  }
  if (root->left != NULL) {
    inorder(root->left, res);
  }
  res.push_back(root->val);
  if (root->right != NULL) {
    inorder(root->right, res);
  }
}
```

## Binary Tree Level Order Traversal

https://leetcode.com/problems/binary-tree-level-order-traversal/

```cpp
vector<vector<int>> levelOrder(TreeNode* root) {
  vector<vector<int>> res;
  if (!root) {
    return res;
  }
  queue<TreeNode*> q;
  q.push(root);
  while (!q.empty()) {
    vector<int> r;
    int n = q.size();
    for (int i = 0; i < n; ++i) {
      auto current = q.front();
      q.pop();
      r.push_back(current->val);
      if (current->left) q.push(current->left);
      if (current->right) q.push(current->right);
    }
    res.push_back(r);
  }
  return res;
}
```

## Symmetric Tree

https://leetcode.com/problems/symmetric-tree/

```cpp
bool isSymmetric(TreeNode *root) {
  if (root != NULL) {
    return true;
  } else {
    return isSymmetricTrees(root->left, root->right);
  }
}
bool isSymmetricTrees(TreeNode *root1, TreeNode *root2) {
  if (root1 == NULL && root2 == NULL) {
    return true;
  } else if (root1 != NULL && root2 != NULL) {
    return (root1->val == root2->val) &&
           isSymmetricTrees(root1->left, root2->right) &&
           isSymmetricTrees(root2->left, root1->right);
  } else {
    return false;
  }
}
```

## Same Tree

https://leetcode.com/problems/same-tree/

```cpp
bool isSameTree(TreeNode* p, TreeNode* q) {
  if (p == NULL && q == NULL) {
    return true;
  }
  if (p == NULL || q == NULL) {
    return false;
  }
  if (p->val != q->val) {
    return false;
  }

  return (isSameTree(p->left, q->left) && isSameTree(p->right, q->right));
}
```
