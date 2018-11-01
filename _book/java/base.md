### Head First Java
#### Java大法好
- 特性：面向对象，内存管理，跨平台可移植性顶呱呱。
- 工作方式：源代码->编译器->输出->JVM(java虚拟机)
- 程序结构：源文件=>类=>方法
- main()是程序运行的起点

##### 类与对象
- 类是对象的蓝图，对象是类的实例。
- 对象包括实例变量以及方法。

##### primitive主数据类型和引用
- 存放数值： byte short int long  float double
- 字符：char
- 布尔 boolean
- 对象引用变量保存的是存取对象的方法，类似指向对象的指针。

##### 对象的行为
- java是值传递
- java的getter是返回实例变量的值，setter是设置实例变量的值
- 封装，将实例变量标记为private。setter以及getter方法标记为public
- 实例变量有默认值。

###### 实例变量以及局部变量的区别
1. 实例变量在类中，局部变量在方法中
2. 局部变量必须初始化

###### 变量的比较
1. ==比较的是两个变量的字节组合。比较引用类型时，判断两个引用是否指向同一个对象。

##### Java的API
###### ArrayList 高级类动态的数组
```
ArrayList<String>  list=new ArrayList <String>();
list.add("dahuang");//添加元素
list.size(); //元素个数
list.remove("danhuang");移除元素
list.remove(0);在引索参数中移除元素
list.contains("dahuang");//匹配则true
list.indexOf("dahuang");//返回引索，无则返-1
list.get(0);返回引索对应的元素
list.isEmpty();//是否为空，空则返true
```
##### 继承和多态
##### 接口和抽象类
 

