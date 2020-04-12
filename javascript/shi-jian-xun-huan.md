#### 事件循环-event loop

js是单线程语言。没得多线程。为啥子没有多线程？js基本上我们用它与用户互动，比如说操作dom等等，如果是多线程就会引起各个同步问题，所以说js为单线程。当然啦，web worker 允许我们创建多个线程，氮素我们的子线程受控于主线程，还不能操作dom，所以其实还是单线程。

当然啦，如果一个任务耗时过长，后面就必须等着，这样也太难受了吧。所以我们的任务就分成2类：

* 宏任务：整体的script，`setTimeout`，`setTnterval`。

* 微任务：`promise` ,`process.nextTick`

事件循环的顺序：先执行整体的script\(宏任务\)，开始第一轮循环。接着执行所有的微任务。然后再从宏任务开始。如此反复。

```
//给一道题自己去体会
console.log('1');

setTimeout(function() {
    console.log('2');
    process.nextTick(function() {
        console.log('3');
    })
    new Promise(function(resolve) {
        console.log('4');
        resolve();
    }).then(function() {
        console.log('5')
    })
})
process.nextTick(function() {
    console.log('6');
})
new Promise(function(resolve) {
    console.log('7');
    resolve();
}).then(function() {
    console.log('8')
})

setTimeout(function() {
    console.log('9');
    process.nextTick(function() {
        console.log('10');
    })
    new Promise(function(resolve) {
        console.log('11');
        resolve();
    }).then(function() {
        console.log('12')
    })
})
```

参考链接：[https://juejin.im/post/59e85eebf265da430d571f89](https://juejin.im/post/59e85eebf265da430d571f89)



