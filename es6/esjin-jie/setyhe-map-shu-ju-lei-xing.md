#### 一.set 无重复数据的集合 键值和键名相等

```
let s = new Set();
[1,1,2,2,3,3,4,4].map(item=>s.add(item))//set 加入值的时候不会进行类型转换
console.log(s)//Set { 1, 2, 3, 4 }
let s = new Set([1,2,3,3,4,"4"]);//Set { 1, 2, 3, 4, '4' }
console.log(s.size)//5
s.delete(1)//Set { 2, 3, 4, '4' }
s.has('4')//true
s.clear();//Set {}

//遍历 keys()：返回键名的遍历器 values()：返回键值的遍历器 entries()：返回键值对的遍历器 forEach()：使用回调函数遍历每个成员
```

#### 二.WeakSet 无重复数据的集合且键值为对象,无法遍历，没有size属性

```
let s = new WeakSet();
let obj={}
s.add(obj)
console.log(s)
```

#### 三.map 键值对的集合

```
let s = new Map();
s.set('name',"danhuang")
s.set('sex',"female")
console.log(s.size)//2
s.get('name')//danhuang
s.has('name')//true
s.delete('name')//true
s.clear()//Map {}
//遍历 keys():返回键名的遍历器 values():返回键值的遍历器。entries():返回所有成员的遍历器。forEach():遍历 Map 的所有成员。

//与其他类型转换
let s = new Map();
s.set('name',"danhuang")
s.set('sex',"female")
console.log([...s])//[ [ 'name', 'danhuang' ], [ 'sex', 'female' ] ] //map转数组
function mapToObj(map){
    let obj={}
    for(let [value,key] of map){
        obj[key]=value
    }
    return obj
}
function objToMap(obj){
    let map=new Map();
   for(let k of Object.keys(obj)){
       map.set(k,obj[k])
   }
    return map
}
let obj=mapToObj(s)
let map=objToMap(obj)
console.log(obj,map)//{ danhuang: 'name', female: 'sex' } Map { 'danhuang' => 'name', 'female' let s = new Map();
s.set('name',"danhuang")
s.set('sex',"female")

let arr=[...s]
console.log(arr)//[ [ 'name', 'danhuang' ], [ 'sex', 'female' ] ]
console.log(new Map(arr)) //Map { 'name' => 'danhuang', 'sex' => 'female' }
function mapToObj(map){
    let obj={}
    for(let [value,key] of map){
        obj[key]=value
    }
    return obj
}
function objToMap(obj){
    let map=new Map();
   for(let k of Object.keys(obj)){
       map.set(k,obj[k])
   }
    return map
}
let obj=mapToObj(s)
let map=objToMap(obj)
console.log(obj,map)//{ danhuang: 'name', female: 'sex' } Map { 'danhuang' => 'name', 'female' => 'sex' }
function mapToJson(map){
    return JSON.stringify([...map])
}
function JsonToMap(json){
    return objToMap(JSON.parse(json))
}
console.log(mapToJson(map))//[["danhuang","name"],["female","sex"]]
console.log(JsonToMap(mapToJson(map)))//Map { '0' => [ 'danhuang', 'name' ], '1' => [ 'female', 'sex' ] }

```

#### 四.WeakMap 只接受键名为对象



