#### 一.线性表的定义：

线性表是n个数据元素的有限序列。特点:有序且有限

#### 二.线性表的顺序表示和实现

###### 线性表的顺序表示是指用一组连续的存储单元依次储存线性表的元素。

1.线性表的顺序实现

```js
//简略代码 其实可以为这个线性表添加 初始化长度的设置 设置完后更改其属性为不可更改 这样就更像c语言的书写方式啦
function OrderedLinkList(){
      this.dataStore=[];
}
//append
OrderedLinkList.prototype.append=function (item){
    this.dataStore.push(item)

//remove 移除所有值为item的元素
OrderedLinkList.prototype.remove=function (item){
    this.dataStore=this.dataStore.join("").replace(item,"").split("");
}

//find 查找 返回的是元素在线性表首次出现的位置
OrderedLinkList.prototype.find=function (item){
    return this.dataStore.indexOf(item)//返回值-1表示不在线性表里面
}

//length
OrderedLinkList.prototype.length=function (){
    return this.dataStore.length
}

//insert  position表示元素的位置
OrderedLinkList.prototype.insert=function (item,position){
     this.dataStore.splice(position,0,item)
}
//测试
var orderedLinkList=new OrderedLinkList()
orderedLinkList.append(1)
orderedLinkList.append(3)
orderedLinkList.append(4)
orderedLinkList.insert(9,2)
console.log(orderedLinkList.dataStore)
console.log(orderedLinkList.length())
```

####  三.线性表的链式表示和实现

###### 线性表的链式表示是指用任意一组储存单元来储存线性表中的数据元素。储存单元可连续也可以不连续

1.单链表实现

```js
//单链表 简略代码

//节点元素
function LinkNode(data,next){
    this.data=data;
    this.next=next;
}
//链表
function LinkList(){
    this.linkNode=new LinkNode(0,null)//这个节点为头节点哟
    this.length=0;//这个是链表长度哟

}
//append
LinkList.prototype.append=function (item){
    this.length++;
    var frontLinkNode=this.linkNode
    while(frontLinkNode.next){
        frontLinkNode=frontLinkNode.next
    }
    var currentLinkNode=new LinkNode(item,null)
    frontLinkNode.next=currentLinkNode
}
//remove 移除所有值为item的元素
LinkList.prototype.remove=function (item){
    var frontLinkNode=this.linkNode
    while(frontLinkNode.next){
        if(frontLinkNode.next.data==item){
            frontLinkNode.next=frontLinkNode.next.next
            this.length--

        }else{
            frontLinkNode=frontLinkNode.next
        }
    }
}
//find 查找 返回的是元素在线性表首次出现的位置
LinkList.prototype.find=function (item){
    var position=0;
    var frontLinkNode=this.linkNode
    while(frontLinkNode.next){
        if(frontLinkNode.next.data==item){
            return position

        }else{
            frontLinkNode=frontLinkNode.next
            position++
        }
    }
    return -1

}
//length
LinkList.prototype.length=function (){
    return this.length
}
//insert  position表示元素的位置
LinkList.prototype.insert=function (item,position){
    //当位置大于链表当前长度时候不进行处理
    if(position+1>this.length){
        return
    }
    var currentPosition=0;
    var frontLinkNode=this.linkNode
    var currentLinkNode=new LinkNode(item,null)
    while(frontLinkNode.next){
        if(currentPosition==position){
            currentLinkNode.next=frontLinkNode.next
            frontLinkNode.next=currentLinkNode
            this.length++
            return
        }else{
            frontLinkNode=frontLinkNode.next
            currentPosition++
        }
    }
}
//测试var list=new LinkList();
list.append(1)
list.append(2)
list.append(3)
list.append(4)
list.remove(3)
list.insert(3,2)
console.log(list.find(4))
```

###### 循环链表是表中最后一个元素的next指向头节点的链表

2.循环链表实现

```
//节点元素
function LinkNode(data,next){
    this.data=data;
    this.next=next;
}
function LinkList(){
    this.linkNode=new LinkNode(0,null)//这个节点为头节点哟
    this.length=0;//这个是链表长度哟

}
//append
LinkList.prototype.append=function (item){
    this.length++;
    var frontLinkNode=this.linkNode
    var currentLinkNode=new LinkNode(item,this.linkNode)
    while(frontLinkNode.next&&frontLinkNode.next!=this.linkNode){
        frontLinkNode=frontLinkNode.next
    }
    frontLinkNode.next=currentLinkNode
}
//remove 移除所有值为item的元素
LinkList.prototype.remove=function (item){
    var frontLinkNode=this.linkNode
    while(frontLinkNode.next&&frontLinkNode.next!=this.linkNode){
        if(frontLinkNode.next.data==item){
            frontLinkNode.next=frontLinkNode.next.next
            this.length--

        }else{
            frontLinkNode=frontLinkNode.next
        }
    }
}
//find 查找 返回的是元素在线性表首次出现的位置
LinkList.prototype.find=function (item){
    var position=0;
    var frontLinkNode=this.linkNode
    while(frontLinkNode.next&&frontLinkNode.next!=this.linkNode){
        if(frontLinkNode.next.data==item){
            return position

        }else{
            frontLinkNode=frontLinkNode.next
            position++
        }
    }
    return -1
}
//length
LinkList.prototype.length=function (){
    return this.length
}
//insert  position表示元素的位置
LinkList.prototype.insert=function (item,position){
    //当位置大于链表当前长度时候不进行处理
    if(position+1>this.length){
        return
    }
    var currentPosition=0;
    var frontLinkNode=this.linkNode
    var currentLinkNode=new LinkNode(item,null)
    while(frontLinkNode.next){
        if(currentPosition==position){
            currentLinkNode.next=frontLinkNode.next
            frontLinkNode.next=currentLinkNode
            this.length++
            return
        }else{
            frontLinkNode=frontLinkNode.next
            currentPosition++
        }
    }
}
//测试
var list=new LinkList();
list.append(1)
list.append(2)
list.append(3)
list.append(4)
list.remove(3)
list.insert(3,2)
console.log(list.find(7))
```

###### 双向链表是有前驱也有后继的链表

3.双向链表的实现

```js
//节点元素
function LinkNode(data,front,next){
    this.data=data;
    this.front=front;
    this.next=next;
}
function LinkList(){
    this.linkNode=new LinkNode(0,null,null)//这个节点为头节点哟
    this.length=0;//这个是链表长度哟

}
//append
LinkList.prototype.append=function (item){
    this.length++;
    var frontLinkNode=this.linkNode
    while(frontLinkNode.next){
        frontLinkNode=frontLinkNode.next
    }
    var currentLinkNode=new LinkNode(item,frontLinkNode)
    frontLinkNode.next=currentLinkNode

}
//remove 移除所有值为item的元素
LinkList.prototype.remove=function (item){
    var frontLinkNode=this.linkNode
    while(frontLinkNode.next){
        if(frontLinkNode.next.data==item){
            frontLinkNode.next=frontLinkNode.next.next
            frontLinkNode.next.front=frontLinkNode
            this.length--

        }else{
            frontLinkNode=frontLinkNode.next
        }
    }
}
//find 查找 返回的是元素在线性表首次出现的位置
LinkList.prototype.find=function (item){
    var position=0;
    var frontLinkNode=this.linkNode
    while(frontLinkNode.next){
        if(frontLinkNode.next.data==item){
            return position

        }else{
            frontLinkNode=frontLinkNode.next
            position++
        }
    }
    return -1

}
//length
LinkList.prototype.length=function (){
    return this.length
}

//insert  position表示元素的位置
LinkList.prototype.insert=function (item,position){
    //当位置大于链表当前长度时候不进行处理
    if(position+1>this.length){
        return
    }
    var currentPosition=0;
    var frontLinkNode=this.linkNode
    while(frontLinkNode.next){
        if(currentPosition==position){
            var currentLinkNode=new LinkNode(item,frontLinkNode)
            currentLinkNode.next=frontLinkNode.next
            frontLinkNode.next.front=currentLinkNode;
            frontLinkNode.next=currentLinkNode
            this.length++
            return
        }else{
            frontLinkNode=frontLinkNode.next
            currentPosition++
        }
    }
}
var list=new LinkList();
list.append(1)
list.append(2)
list.append(3)
list.append(4)
list.remove(3)
list.insert(3,2)
console.log(list.find(4))
```

-2019.4.20

