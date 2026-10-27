# Leetcode_Day87
# Day 87: Same Tree

**LeetCode Problem:** 100. Same Tree  
**Difficulty:** Easy  
**Language:** Java  
**Topics:** Binary Tree, Recursion, Tree Traversal

## Problem Statement

Given the roots of two binary trees, `p` and `q`, determine whether they are the same.

Two binary trees are considered the same if:
- They have the same structure.
- Their corresponding nodes contain the same values.

## Approach: Recursion

I solved this problem using recursion to compare the two trees node by node.

### Steps

1. If both nodes are `null`, return `true` because both trees are empty at that position.
2. If only one node is `null`, return `false` because the tree structures are different.
3. If the values of the two nodes are different, return `false`.
4. Recursively compare their left subtrees.
5. Recursively compare their right subtrees.
6. Return `true` only if both subtree comparisons are successful.

## Java Solution

```java
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {
        if (p == null && q == null) {
            return true;
        }

        if (p == null || q == null) {
            return false;
        }

        if (p.val != q.val) {
            return false;
        }

        return isSameTree(p.left, q.left)
            && isSameTree(p.right, q.right);
    }
}
```

## Example

**Input:**
```text
p = [1,2,3]
q = [1,2,3]
```

**Output:**
```text
true
```

**Explanation:**

Both trees have the same structure and corresponding nodes contain the same values. Therefore, the trees are identical.

## Complexity Analysis

Let `n` be the number of nodes in the smaller tree.

- **Time Complexity:** O(n) when both trees have the same number of nodes. More generally, the algorithm takes O(min(P, Q)) time if a mismatch is found early, and at most O(min(P, Q)) node comparisons, where P and Q are the respective tree sizes.
- **Space Complexity:** O(h), where `h` is the maximum recursion depth. In the worst case, this can be O(n).

## What I Learned

- How to compare two binary trees using recursion.
- Why checking `null` nodes is essential when comparing tree structures.
- How to compare corresponding node values.
- How recursion helps break a larger problem into smaller subproblems.

## Key Observation

Two trees are identical only when their structures and corresponding node values match.

Checking just the root values is not enough. Every corresponding node must satisfy the same conditions.

## Takeaway

This problem reinforced the importance of checking both structure and values. In coding, two things can look similar at first, but careful comparison is what confirms whether they are truly the same.
