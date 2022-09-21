# CSCI 570 - Homework 04

- **Author:** Boyang Xiao
- **Due Date:** Sep. 21<sup>th</sup> 2022
- **USC id**: 3326-7302-74
- **Email**: <a href="mailto:boyangxi@usc.edu">boyangxi@usc.edu</a>

---

### Problem 1

#### Answer:

- #### My data structure designing:

My data structure, lets call it Median Heap, is a binary tree very similar to the max heap or the min heap. The median heap has a root node, which should always saves the median value. And the root nodes has two childen, who are the roots for their own sub-trees. The left sub-tree should be a max heap and the right sub-tree should be a min heap. And the size of them should be the same or at most 1 items greater than the other one. The left subtree's nodes should all have smaller values than the whole root node, and the right subtree's nodes should all have larger or equal values than the whole root node. In this way, to get the median value, we can simply extract the root node's value or extract the mean of the root node and one of its child node. Also, the insertion operation should only go down to the level of the tree, which takes $O(logn)$.

- #### Methods of the Median heap:

```python
MedianHeap::Find-Median(){
    if(sizeof left_tree == sizeof right_tree)
        return rootNode.val;
    else if(sizeof left_tree > sizeof right_tree)
        return (left_tree_root.val + root.val) / 2;
    else if(sizeof left_tree < sizeof right_tree)
        return (right_tree_root.val + root.val) / 2;
}
```

```cpp
MedianHeap::Insert(HeapNode root, float new_val){
    // We use recursion to insert the item recursively to the whole heap
    if(new_val < root.val)
        Push new_val to the end of the left tree
        Trickle it up to make the left tree to be a max Heap
        sizeof left_tree ++;
    else if(new_val >= root.val)
        Push new_val to the end of the right tree
        Trickle it up to make the right tree to be min heap
        sizeof right_tree ++;
    
    if(diff(sizeof left_tree, sizeof right tree) > 1)
        Move the root from the larger side to the smaller side's root;
        Adjust the left and right sub-trees to be a max/min heap;
}
```
---

### Problem 2

#### Answers


