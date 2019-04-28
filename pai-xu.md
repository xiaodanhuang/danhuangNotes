#### 七大查找算法

#### 1.顺序查找

###### 原理：依次将扫描到的结点关键字与给定值k相比较

```js
function orderedSearch(arr,num){
    for(var i=0;i<arr.length;i++){
        if(num==arr[i]){
            return true
        }
    }

    return false
}

var arr=[7,6,9,4,0,5]
console.log(orderedSearch(arr,9))
console.log(orderedSearch(arr,-1))
```

#### 2.二分查找

###### 原理：有序查找算法。用给定值k先与中间结点的关键字比较，中间结点把线形表分成两个子表，若相等则查找成功；若不相等，继续

```js
function binarySearch(arr,item){
    var low=0,high=arr.length-1;
    while(low<=high){
        var mid= low+ Math.floor((high-low)/2)
        if(arr[mid]==item){
            return mid
        }else if(item<arr[mid]){
            high=mid-1
        }else{
            low=mid+1
        }
    }
    return -1
}
```

#### 3.插入查找

```js
function insertSearch(arr,item){
    var low=0,high=arr.length-1;
    while(low<=high){
        var mid= low+Math.floor((item-arr[low])/(arr[high]-arr[low])*(high-low))
        if(arr[mid]==item){
            return mid
        }else if(item<arr[mid]){
            high=mid-1
        }else{
            low=mid+1
        }
    }
    return -1
}

```



