#### 一.树

###### 树型结构是非线性结构，是由n个节点组成的有限集合。

#### 二.二叉树

###### 二叉树是一种特殊的树型结构。特点是它的每个节点至多只有2棵子树，分为左子树和右子树。

1.二叉树的创建

```
function Node(data,left,right){
    this.data=data;
    this.left=left;
    this.right=right;

}
function BST(){
    this.root=null;
}
BST.prototype.insert=function(data){
    var node=new Node(data,null,null)
    if(this.root==null) {
        this.root = node
        return
    }
    var current=this.root;
    while(true){
        var parent=current;
        if(data<current.data){
            current=current.left;
            if(current==null){
                parent.left=node
                return
            }
        }else{
            current=current.right;
            if(current==null){
                parent.right=node
                return
            }
        }
    }
}
```

#### 三.二叉树的遍历

1.二叉树的中序遍历

###### 中序遍历左中右

代码实现：

```js
//inOrder
BST.prototype.inOrder=function(node){
    if(!node){
        return
    }
    arguments.callee(node.left)
    console.log(node.data)
    arguments.callee(node.right)
}
var bst= new BST();
bst.insert(23)
bst.insert(45)
bst.insert(16)
bst.insert(37)
bst.insert(3)
bst.insert(99)
bst.insert(22)
bst.inOrder(bst.root)
//输出为：3,16,22,23,37,45,99
```

2.二叉树的先序遍历

先序中左右

代码实现：

```
//preOrder
BST.prototype.preOrder=function(node){
    if(!node){
        return
    }
    console.log(node.data)
    arguments.callee(node.left)
    arguments.callee(node.right)
}
//输出为： 23, 16, 3, 22, 45, 37, 99
```

3.二叉树的后序遍历

后序左右中

代码实现:

```
//afterOrder
BST.prototype.afterOrder=function(node){
    if(!node){
        return
    }
    arguments.callee(node.left)
    arguments.callee(node.right)
    console.log(node.data)
    afterOrderList.push(node.data)
}
//输出为 3, 22, 16, 37, 99, 45, 23
```

-2019.04.21

