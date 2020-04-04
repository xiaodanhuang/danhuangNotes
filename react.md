> #### 与Vue的对比

1. 数据监听方式不同

   Vue：通过Object.defineProperty结合发布者监听者模式 对数据进行精准的监听。**讲究数据可变性**。**（vuex同讲究数据可变）**

   React：通过比较引用的形式对数据进行监听。**讲究数据不可变性。（redux同讲究数据不可变）**

2. 数据流向不同

   Vue： v1.x可以实现2种双向绑定，v2.使用单向数据流

   React：单向数据流

3. 代码的复用以及其他

   Vue :使用minxins

   React：使用 hoc/render props

4. 组件的通信方式

   Vue:

         props /emit



         event bus ：emit /on



         provide /inject



   React:



        props



        ref



        context

5.渲染方式不同

Vue：扩展HTML的形式   **指令**

React：JSX  **原生JS**

[https://juejin.im/post/5b8b56e3f265da434c1f5f76\#heading-4](https://juejin.im/post/5b8b56e3f265da434c1f5f76#heading-4 "资料来源")

