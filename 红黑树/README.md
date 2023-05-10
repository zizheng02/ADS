# 红黑树(代码未实现)

红黑树是一种**自平衡的二叉搜索树**。每个节点额外存储了一个 color 字段 ("RED" or "BLACK")，用于确保树在插入和删除时保持平衡。

> 红黑树并不是一个完美平衡二叉查找树, 但黑色节点的层数是相同的, 称为**黑色完美平衡**

### 性质

1. 节点为红色或黑色
2. 根节点是黑色
3. NIL 节点（空叶子节点）为黑色
4. 红色节点的子节点为黑色(即不存在连续两个红色节点)
5. 任意一结点到每个叶子结点的路径都包含数量相同的黑结点。

### 节点维护的信息

| Identifier | Type                  | Description                    |
| :--------- | :-------------------- | :----------------------------- |
| `left`     | `Node*`               | 左子节点指针                   |
| `right`    | `Node*`               | 右子节点指针                   |
| `parent`   | `Node*`               | 父节点指针                     |
| `color`    | `enum { BLACK, RED }` | 颜色枚举                       |
| `key`      | `Key`                 | 节点键值，具有唯一性和可排序性 |
| `value`    | `Value`               | 节点内储存的值                 |

### Rebalance

三种操作：左旋、右旋和变色。

- **左旋**：以某个结点作为支点(旋转结点)，其右子结点变为旋转结点的父结点，右子结点的左子结点变为旋转结点的右子结点，左子结点保持不变。
- **右旋**：以某个结点作为支点(旋转结点)，其左子结点变为旋转结点的父结点，左子结点的右子结点变为旋转结点的左子结点，右子结点保持不变。
- **变色**：结点的颜色由红变黑或由黑变红。

![img](https://upload-images.jianshu.io/upload_images/2392382-a95db442f1b47f8a.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)

![img](https://upload-images.jianshu.io/upload_images/2392382-0676a8e2a12e2a0b.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)

我们先忽略颜色，可以看到旋转操作不会影响旋转结点的父结点，父结点以上的结构还是保持不变的。
 **左旋**只影响旋转结点和其**右子树**的结构，把右子树的结点往左子树挪了。
 **右旋**只影响旋转结点和其**左子树**的结构，把左子树的结点往右子树挪了。

### 插入

先假设插入的都是红色节点(不破坏黑色完美平衡)

![img](https://upload-images.jianshu.io/upload_images/2392382-fa2b78271263d2c8.png?imageMogr2/auto-orient/strip|imageView2/2/w/1033/format/webp)

![img](https://upload-images.jianshu.io/upload_images/2392382-9ac3d6b69ef7ead3.png?imageMogr2/auto-orient/strip|imageView2/2/w/662/format/webp)

### 删除

> 和插入一样也是分情况讨论



---

### 参考资料

- [30张图带你彻底理解红黑树 - 简书 (jianshu.com)](https://www.jianshu.com/p/e136ec79235c)

  