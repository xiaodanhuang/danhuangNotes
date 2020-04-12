#### 异步解决方案

* 回调函数
* Promise

所谓`Promise`，简单说就是一个容器，里面保存着某个未来才会结束的事件（通常是一个异步操作）的结果。从语法上说，Promise 是一个对象，从它可以获取异步操作的消息。Promise 提供统一的 API，各种异步操作都可以用同样的方法进行处理。

特点：

* 有三种状态：`pending` \(进行中\)，`fulfilled `\(成功\)，`rejected` \(失败\)
* 一旦状态改变，就不会再变，任何时候都可以得到这个结果。`Promise`对象的状态改变，只有两种可能：从`pending`变为`fulfilled`和从`pending`变为`rejected`。只要这两种情况发生，状态就凝固了，不会再变了，会一直保持这个结果，这时就称为 resolved（已定型）。const PENDING = 'pending', FULFILLED = 'fulfilled', REJECTED = 'rejected'

```
class Promise {
    constructor(executor) {
        this.state = PENDING;
        this.data = undefined;
        this.reason = undefined;
        this.onResolvedCallBacks = [];
        this.onRejectedCallBacks = [];
        const resolve = (data) => {
            if (this.state === PENDING) {
                this.state = FULFILLED;
                this.data = data;
                this.onResolvedCallBacks.forEach(fn => fn(data))
            }
        }
        const reject = (reason) => {
            if (this.state === PENDING) {
                this.state = REJECTED
                this.reason = reason;
                this.onResolvedCallBacks.forEach(fn => fn(reason));
            }
        }
        try {
            executor(resolve, reject)
        } catch (e) {
            reject(e)
        }
    }

    then(onFulfilled, onRejected) {
        if(typeof onFulfilled !=='function'){
            onFulfilled=value=>value;
        }
        if(typeof onRejected!=='function'){
            onRejected=(error)=>{throw new Error(error)}

        }
        let promise2 = new Promise((resolve, reject) => {
            if (this.state === FULFILLED) {
                let x = onFulfilled(this.value);
                resolePromise(promise2, x, resolve, reject)
            }
        })
        if (this.state === FULFILLED) {
            onFulfilled();
        }
        if (this.state === onRejected) {
            onRejected()
        }
        if (this.state === PENDING) {
            this.onResolvedCallBacks.push(onFulfilled);
            this.onRejectedCallBacks.push(onRejected)
        }
        return promise2;
    }
}

function resolvePromise(x, promise2, resolve, reject) {
    //循环引用报错
    if (x === promise2) {
        //reject报错
        return reject(new Error('chaining cycle detected'))
    }
    let called;
    if (x !== null && typeof x === 'function' && typeof x === 'object') {
        try {
            let then = x.then;
            if (typeof x === 'function') {
                then.call(x,
                    y => {
                        if (called) return;
                        called = true;
                        resolvePromise(promise2, y, resolve, reject)
                    },
                    err => {
                        if (called) return;
                        called = true;
                        reject(err)
                    }
                )
            } else {
                resolve(x)
            }
        }
        catch (e) {
            if (called) return;
            called = true;
            reject(e)
        }
    } else {
        resolve(x)
    }

}
```

* async await





