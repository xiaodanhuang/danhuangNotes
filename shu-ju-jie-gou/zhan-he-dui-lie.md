#### 一.栈

###### 限定仅在表尾进行插入或删除操作的线性表

1.顺序栈的实现

```js
function Stack(){
    this.dataStore=[];
}
Stack.prototype.push=function(item){
    this.dataStore.push(item);

}
Stack.prototype.pop=function(item){
    this.dataStore.pop();

}
Stack.prototype.length=function(item){
   return this.dataStore.length;

}
Stack.prototype.clear=function(item){
     this.dataStore=[];

}
Stack.prototype.top=function(){
    return this.dataStore[this.dataStore.length-1]
}
 var stack=new Stack()
stack.push(1)
stack.push(2)
stack.push(3)
stack.push(4)
stack.pop();
console.log(stack.length())
console.log(stack.top())
stack.clear()
console.log(stack.dataStore)
```

2.链式栈的实现

```js
function LinkNode(data,next){
    this.data=data;
    this.next=next;

}
function Stack(){
    this.linkNode=new LinkNode(0,null)
    this.size=0;
}
Stack.prototype.push=function(data){
    var frontLinkNode=this.linkNode;
    while(frontLinkNode.next){
        frontLinkNode=frontLinkNode.next;
    }
    var currentLinkNode=new LinkNode(data,null)
    frontLinkNode.next=currentLinkNode;
    this.size++
}
Stack.prototype.pop=function(){
    var frontLinkNode=this.linkNode;
    while(frontLinkNode.next&&frontLinkNode.next.next!=null){
        frontLinkNode=frontLinkNode.next;
    }
    frontLinkNode.next=null;
    this.size--
}
Stack.prototype.length=function(item){
    return this.size;

}

Stack.prototype.clear=function(item){
    this.size=0;
    this.linkNode.next=null;
}
Stack.prototype.top=function(){
    var frontLinkNode=this.linkNode;
    while(frontLinkNode.next){
        frontLinkNode=frontLinkNode.next;
    }
    return frontLinkNode.data

}

var stack=new Stack()
stack.push(1);
stack.push(2);
stack.push(3);
stack.pop()
console.log(stack.top())
console.log(stack.length())
stack.clear()
console.log(stack)
```

#### 二.队列

仅在队首删除和在队尾添加的线性表

1.顺序队列的实现

```js
function Queque(){
    this.dataStore=[]
}
Queque.prototype.push=function(item){
    this.dataStore.push(item);

}
Queque.prototype.shift=function(){
    this.dataStore.shift();

}
Queque.prototype.length=function(){
    return this.dataStore.length;

}
Queque.prototype.clear=function(){
    this.dataStore=[];

}
var queque=new Queque()
queque.push(1)
queque.push(2)
queque.push(3)
queque.push(4)
queque.shift();
console.log(queque.length())
queque.clear()
console.log(queque.dataStore)
```

2.链栈的实现

```js
function LinkNode(data,next){
    this.data=data;
    this.next=next;
}
function Queque(){
    this.linkNode=new LinkNode(0,null)
    this.size=0;
}
Queque.prototype.push=function(data){
    var frontLinkNode=this.linkNode;
    while(frontLinkNode.next){
        frontLinkNode=frontLinkNode.next;
    }
    var currentLinkNode=new LinkNode(data,null)
    frontLinkNode.next=currentLinkNode;
    this.size++
}
Queque.prototype.shift=function(){
    var currentNode=this.linkNode.next;
    this.linkNode.next=this.linkNode.next.next;
    this.size--;
    return currentNode.data


}
Queque.prototype.length=function(item){
    return this.size;

}

Queque.prototype.clear=function(item){
    this.size=0;
    this.linkNode.next=null;
}
var queque=new Queque()
queque.push(1)
queque.push(2)
queque.push(3)
queque.push(4)
console.log(queque.shift())
queque.clear()
```

-2019.04.21

