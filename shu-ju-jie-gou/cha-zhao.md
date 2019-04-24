#### 几大查找算法

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

原理：将一个元素插入到一个有序列表中

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

原理：取增量，进行分组排，再进行插入排序

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



