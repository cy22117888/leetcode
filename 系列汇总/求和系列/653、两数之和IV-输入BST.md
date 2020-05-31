653、两数之和IV-输入BST
===

给定一个二叉搜索树和一个目标结果，<br>
如果 BST 中存在两个元素且它们的和等于给定的目标结果，则返回 true。<br>

案例 1:<br>
```
输入: 
    5
   / \
  3   6
 / \   \
2   4   7

Target = 9

输出: True
```

案例 2:<br>
```
输入: 
    5
   / \
  3   6
 / \   \
2   4   7

Target = 28

输出: False
```
``
来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/two-sum-iv-input-is-a-bst
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
``

### 方法1：BST的中序遍历，将题目转换为有序集合的两数之和问题
```
public boolean findTarget(TreeNode root, int k) {
    // 思路1：
    // 首先，对BST进行中序遍历，用ArrayList储存节点值
    traverse(root);
    // 之后，题目可视为在一个集合中寻找两数之和(左右指针夹逼法))
    int l = 0, r = this.list.size() - 1;
    while (l < r) {
        int sum = this.list.get(l) + this.list.get(r);
        if (sum == k) return true;
        else if (sum > k) r --;
        else l ++; 
    }
    return false;
}

// BST的中序遍历
private void traverse(TreeNode root) {
    // 左
    if (root.left != null) traverse(root.left);
    // 中
    this.list.add(root.val);
    // 右
    if (root.right != null) traverse(root.right);
}
```

### 方案2：BST中的极值搜索
```
private TreeNode root;
private int k;

public boolean findTarget(TreeNode root, int k) {
    // 思路2：
    // 递归寻找
    this.root = root;
    this.k = k;
    return dfs(root);
}

// 深度优先遍历
private boolean dfs(TreeNode currentNode) {
    // base case
    if (currentNode == null) return false;
    // 当前层逻辑
    TreeNode node = find(root, k - currentNode.val);
    if (node != null && node != currentNode) return true;
    // 向下递归
    return dfs(currentNode.left) || dfs(currentNode.right);
}

// 寻找另一个值的底层实现
private TreeNode find(TreeNode current, int target) {
    // base case
    if (current == null) return null;
    if (target == current.val) return current;

    return target > current.val ? find(current.right, target) : find(current.left, target);
}
```
