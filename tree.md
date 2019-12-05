+ [Path Sum](#path-sum)
+ [Path Sum II](#path-sum-ii)
+ [Maximum Depth of Binary Tree](#maximum-depth-of-binary-tree)
+ [Maximum Depth of N-ary Tree](#maximum-depth-of-n-ary-tree)
+ [Binary Tree Inorder Traversal](#binary-tree-inorder-traversal)
+ [Binary Tree Level Order Traversal](#binary-tree-level-order-traversal)
+ [Symmetric Tree](#symmetric-tree)
+ [Same Tree](#same-tree)
+ [Invert Binary Tree](#invert-binary-tree)
+ [Subtree of Another Tree](#subtree-of-another-tree)
+ [Kth Smallest Element in a BST](#kth-smallest-element-in-a-bst)
+ [Validate Binary Search Tree](#validate-binary-search-tree)
+ [Lowest Common Ancestor of a Binary Tree](#lowest-common-ancestor-of-a-binary-tree)
+ [Binary Search Tree Iterator](#binary-search-tree-iterator)

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

## Invert Binary Tree

https://leetcode.com/problems/invert-binary-tree/

```cpp
TreeNode* invertTree(TreeNode* root) {
  if (root != NULL) {
    TreeNode* left = invertTree(root->right);
    root->right = invertTree(root->left);
    root->left = left;
  }
  return root;
}
```

## Subtree of Another Tree

https://leetcode.com/problems/subtree-of-another-tree/

```cpp
bool isSubtree(TreeNode* s, TreeNode* t) {
  if (s == NULL && t == NULL) {
    return true;
  }
  if (t == NULL) {
    return true;
  } else if (s == NULL) {
    return false;
  }

  return (isSameTree(s, t) || isSubtree(s->left, t) || isSubtree(s->right, t));
}
bool isSameTree(TreeNode* s, TreeNode* t) {
  if (s == NULL && t == NULL) {
    return true;
  }
  if (s == NULL || t == NULL) {
    return false;
  }
  if (s->val != t->val) {
    return false;
  }

  return (isSameTree(s->left, t->left) && isSameTree(s->right, t->right));
}
```

## Kth Smallest Element in a BST

https://leetcode.com/problems/kth-smallest-element-in-a-bst/

```cpp
int kthSmallest(TreeNode* root, int k) { 
  return Smallest(root, k); 
}
int Smallest(TreeNode* root, int& k) {
  if (root == NULL) {
    return 0;
  }
  int res = Smallest(root->left, k);
  if (k == 0) {
    return res;
  }
  if (--k == 0) {
    return root->val;
  }
  return Smallest(root->right, k);
}
```

## Validate Binary Search Tree

https://leetcode.com/problems/validate-binary-search-tree/

```cpp
bool isValidBST(TreeNode* root) {
  return Validate(root, LONG_MIN, LONG_MAX);
}
bool Validate(TreeNode* root, long min, long max) {
  if (root == NULL) {
    return true;
  }
  if ((root->val <= min) || (root->val >= max)) {
    return false;
  }
  return Validate(root->left, min, root->val) &&
         Validate(root->right, root->val, max);
}
```

## Lowest Common Ancestor of a Binary Tree

https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/

```cpp
TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
  if (root == NULL || root == p || root == q) return root;
  TreeNode* left = lowestCommonAncestor(root->left, p, q);
  TreeNode* right = lowestCommonAncestor(root->right, p, q);
  if (left == NULL) {
    return right;
  } else {
    if (right == NULL) {
      return left;
    } else {
      return root;
    }
  }
}
```

## Binary Search Tree Iterator

https://leetcode.com/problems/binary-search-tree-iterator/

```cpp
stack<TreeNode*> st;
BSTIterator(TreeNode* root) {
  find_left(root); 
}

/** @return whether we have a next smallest number */
bool hasNext() {
  return !st.empty(); 
}

/** @return the next smallest number */
int next() {
  TreeNode* top = st.top();
  st.pop();
  if (top->right != NULL) {
  find_left(top->right);
  }
  return top->val;
}

/** put all the left child() of root */
void find_left(TreeNode* root) {
  TreeNode* p = root;
  while (p != NULL) {
    st.push(p);
    p = p->left;
  }
}
```
