#### 十大排序算法

#### 1.冒泡排序

###### 原理：比较两个相邻的元素，将值大的元素交换至右端

###### N个数字要排序完成，总共进行N-1趟排序，每趟的排序次数为\(N-i\)次

```js
function bubbleSort(arr){
   for(var j=0;j<arr.length-1;j++){
       for(var i=0;i<arr.length-1-j;i++){
           if(arr[i]>arr[i+1]){
               swap(arr,i,i+1)
           }
       }
   }
}

function swap(arr,i,j){
    var current=arr[i];
    arr[i]=arr[j]
    arr[j]=current
}
var arr=[7,6,9,4,0,5]
bubbleSort(arr)
console.log(arr)
```

#### 2.选择排序

###### 原理：每一趟从待排序的排序的记录中选出最小的放到已经排好的记录后面

```
function chooseSort(arr) {
    for(var i=0;i<arr.length-1;i++){
        for(var j=i+1;j<arr.length;j++){
            if(arr[i]>arr[j]){
                swap(arr,i,j)
            }
        }
    }

}
function swap(arr,i,j){
    var current=arr[i];
    arr[i]=arr[j]
    arr[j]=current
}
var arr=[7,6,9,4,0,5]
chooseSort(arr)
console.log(arr)
```

#### 3.插入排序

###### 原理：将一个元素插入到一个有序列表中

```js
function insertSort(arr){
    for(var i=1;i<arr.length;i++){
        for(var j=i;j>=0;j--){
            if(arr[j]<arr[j-1]){
                swap(arr,j,j-1)
            }
        }
    }
}
function swap(arr,i,j){
    var current=arr[i];
    arr[i]=arr[j]
    arr[j]=current
}

var arr=[7,6,9,4,0,5]
insertSort(arr)
console.log(arr)
```

-2019.04.21

#### 4.希尔排序ps:这个排序忘记怎么写了又看书了

###### 原理：取增量，进行分组排，再进行插入排序

```js
function shellSort(arr,gap){
    while(gap) {
        for (var i = 0; i < arr.length; i++) {
            for (var j = i; j >gap-1; j-=gap) {
                if (arr[j] <arr[j-gap]) {
                    swap(arr, j-gap, j)
                }
            }
        }
       gap=Math.floor(gap/2)
    }
}
function swap(arr,i,j){
    var current=arr[i];
    arr[i]=arr[j]
    arr[j]=current
}

var arr=[7,6,9,4,0,5]
shellSort(arr,10)
console.log(arr)
```

#### 5.归并排序

###### 原理：将数组分成2个数组排好序合在一起 ，2个小数组再分再he.....

```js
//归并
function mergeSort(arr,left,right){
    if(left==right){
        return
    }
    var mid=left+ Math.floor((right-left)/2)
    mergeSort(arr,left,mid)
    mergeSort(arr,mid+1,right)
    mergeArr(arr,left,mid+1,right)


}
//合并数组
function mergeArr(arr,left,right,rightBound){
    var new_arr=[]
    var  i=left,j=right;
    while(i<right&&j<=rightBound){
        new_arr.push(arr[i]<arr[j]?arr[i++]:arr[j++])
    }
    while(i<right){
        new_arr.push(arr[i++])
    }
    while(j<=rightBound){
        new_arr.push(arr[j++])
    }
    for(var i=0;i<new_arr.length;i++){
        arr[left+i]=new_arr[i]
    }
}
```

#### 6快速排序

###### 原理：以某个数为基准 ，比他小的放它左边，比他大的放它右边

```js
function quickSort(arr,left,right){
    if(left>=right) return
    var mid=partition(arr,left,right)
    quickSort(arr,left,mid-1)
    quickSort(arr,mid,right)
}
function partition(arr,left,right){

    var i=left,j=right,p=arr[right];
    while(i<j){
        while(i<j&&arr[i++]<=p)
        {i++};
        while(i<j&&arr[j]>=p)
        {j--};
        if(i<j){
            swap(arr,i,j)
        }
    }
    swap(arr,i,right)
    return i;

}
function swap(arr, i, j) {
    var a = arr[i]
    arr[i] = arr[j];
    arr[j] = a;
}

var arr=[7,3,2,8,1,9,6,7,5,4,6,10]
quickSort(arr,0,arr.length-1)
console.log(arr)
```

#### 7.堆排序

###### 原理：构造完全二叉树 进行调换排序

```js
//堆排序
function heapSort(arr){
    for(var j=arr.length-1;j>=0;j--) {
        for (var i = Math.floor((j - 1) / 2); i >= 0; i--) {
            heapify(arr,j, i)
        }
        swap(arr,0,j)
    }
}
function heapify(arr,j,i){
    var  left=j>=2*i+1?2*i+1:null;
    var  right=j>=2*i+2?2*i+2:null;
    var max=i
    if(left){
        max=arr[left]>arr[i]?left:i

    }
    if(right){
        max=arr[right]>arr[max]?right:max

    }
    if(max!=i){
        swap(arr,max,i)
        heapify(arr,max)
    }
}

function swap(arr, i, j) {
    var a = arr[i]
    arr[i] = arr[j];
    arr[j] = a;
}
var heap=[2,5,3,1,10,4]
heapSort(heap)
console.log(heap)
```

#### 8.计数排序

###### 原理：计数排序的核心在于将输入的数据值转化为键存储在额外开辟的数组空间中，使用此法，必须是整数的排序。

```js
function countingSort(arr,max){
    var bucket=new Array(max+1)//其实这个max 有没有都无所谓，毕竟js
    for(var i=0;i<arr.length;i++){
        if(!bucket[arr[i]]){
        bucket[arr[i]]++
    }
    var sortedIndex=0;
    for(var j=0;j<bucket.length;j++){
        while(bucket[j]){
            arr[sortedIndex++]=j
            bucket[j]--
        }

    }


}
function max(arr) {
    var max=0
   for(var i=0;i<arr.length;i++){

       max=max<arr[i]?arr[i]:max
   }
   return max
}
var arr=[2,1,7,8,3,6,9]
countingSort(arr, max(arr))
console.log(arr)
```

#### 9.桶排序

###### 原理:升级版的计数排序

```js
function bucketSort(arr){
    var min=arr[0],max=arr[0];
    for(i=0;i<arr.length;i++){
        min=min>arr[i]?arr[i]:min;
        max=max<arr[i]?arr[i]:max
    }
    var bucketSize=5;
    var bucketCount=Math.floor((max-min)/bucketSize)+1
    var bucket=new Array(bucketCount);
    for( var j=0;j<arr.length;j++){
        bucket[j]=[]
    }

    arr.map(item=>{
        bucket[Math.floor((item - min) / bucketSize)].push(item);
    })
    arr=[]
    bucket.map(item=>{
        item.sort()
        arr=arr.concat(item)
    })
    return arr
}
var arr=[7,6,9,4,0,5]

console.log(bucketSort(arr))
```

#### 10.基数排序

###### 原理：根据键值的每位数字来分配桶

```js
function lsdRadixSort(arr,max){
    var num=0,sortIndex=0;
    while(Math.floor(max/10)){
        num++
        max/=10
    }
    while(sortIndex<=num){
        arr=bucket(arr,sortIndex)
        console.log(arr)
        sortIndex++
    }

}
function bucket(arr,num){
    var bucket=[];
    for(var i=0;i<10;i++){
        bucket[i]=[]
    }
    arr.map(item=>{

        bucket[Math.floor(item/Math.pow(10,num))%10].push(item);
    })
    arr=[];
    bucket.map(item=>{
        arr=arr.concat(item)
    })

    return  arr

}
function max(arr) {
    var max=0
    for(var i=0;i<arr.length;i++){

        max=max<arr[i]?arr[i]:max
    }
    return max
}

var arr=[170,45,75,90,802,2,24,66];
lsdRadixSort(arr,max(arr))
```

-2019.4.28

