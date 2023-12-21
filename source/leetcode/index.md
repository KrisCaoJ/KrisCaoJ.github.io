---
title: leetcode
date: 2023-12-21 17:35:10
---
class TreeNode():
    """
        定义树节点
    """

    def __init__(self, data, left=None, right=None):
        self.left = left
        self.right = right
        self.data = data


""" 完全二叉树"""


class BinaryTree():
    """" 定义初始化函数"""

    def __init__(self):
        self.root = None
        self.Is = []  # 定义一个列表，用于存储节点地址

    """ 定义元素添加方法"""

    def add(self, data):
        node = TreeNode(data)
        if self.root == None:
            self.root = node
            self.Is.append(self.root)
        else:
            rootNode = self.Is[0]
            if rootNode.left == None:
                rootNode.left = node
                self.Is.append(rootNode.left)
            elif rootNode.right == None:
                rootNode.right = node
                self.Is.append(rootNode.right)
                self.Is.pop(0)

    """
        针对add函数添加的说明：
            1. 对于self.root == None，判断二叉树的根节点是否为空，为空则先添加根节点的值，之后将根节点放入Is列表
            2. 对于一般的节点添加，先读取Is列表的第一个节点地址，判断其左右子节点是否为空，依次添加，后从Is列表弹出该节点
            3. 该添加顺序是以3个节点，即一个深度为1的二叉树进行添加，添加完毕后再以子节点为根节点继续添加
    """

    def preOderTraversal(self, root):
        if root is None:
            return
        print(root.data)
        self.preOderTraversal(root.left)
        self.preOderTraversal(root.right)
    def inOrderTraversal(self,root):
        if root is None:
            return
        self.inOrderTraversal(root.left)
        print(root.data)
        self.inOrderTraversal(root.right)
    def postOrderTraversal(self,root):
        if root is None:
            return
        self.postOrderTraversal(root.left)
        self.postOrderTraversal(root.right)
        print(root.data)
    def levelTraversal(self,root):
        if root == None:
            return
        queue = []
        result = []
        node = root
        queue.append(root)
        while queue:
            node = queue.pop(0)
            result.append(node.data)
            if node.left != None:
                queue.append(node.left)
            if node.right != None:
                queue.append(node.right)
    """
        
    """
tree = BinaryTree()
for i in range(1, 11):
    tree.add(i)
tree.preOderTraversal(tree.root)
