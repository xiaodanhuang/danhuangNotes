#### 深拷贝和浅拷贝

js中数据类型分为基本数据类型和引用数据类型**。**基本数据类型保存在栈上，而引用数据类型的值保存的是一个指针，这个指针指向存在堆上的一个对象。

当我们从一个变量向另一个变量复制引用类型的值时，实际上是将这个引用类型在栈内存中的引用地址复制了一份给新的变量，其实就是一个指针。因此当操作结束后，这两个变量实际上指向的是同一个在堆内存中的对象，改变其中任意一个对象，另一个对象也会跟着改变。所以深拷贝和浅拷贝只存在于引用类型当中。

##### 浅拷贝

只会将对象的各个属性进行依次复制，并不会进行递归复制，也就是说只会赋值目标对象的第一层属性。

##### 常用的浅拷贝函数

```
//数组的拷贝
Array.concat();
[...array]
//对象的拷贝
Object.assign(target,source);
{...}
```

##### 

##### **深拷贝**

不同于浅拷贝，它不只拷贝目标对象的第一层属性，而是`递归`拷贝目标对象的所有属性。

##### 常用的深拷贝函数

```
//可以解决平时的问题，但是无法解决循环引用等问题
JSON.parse();
JSON.stringfy();
```

蛋黄手写版（可能有bug）

```
function deepClone(obj,map=new WeakMap()){
    if(map.has(obj)) return obj
    if(obj instanceof RegExp) return new RegExp(obj)
    if(obj instanceof Date) return new Date(obj)
    if(obj ===null||typeof obj !="object") return obj
    let objClone=Array.isArray(obj)?[]:{};
    map.set(obj,objClone)
    for(key in obj){
        if(obj.hasOwnProperty(key)){
            if(typeof obj[key]!=='object'){
                objClone[key]=obj[key]
            }else{
                objClone[key]=deepClone(obj[key],map)
            }
        }
    }
    return objClone
}
```



