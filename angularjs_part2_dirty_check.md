# 脏检查机制

Angular将双向绑定转换为一堆watch表达式，然后递归检查这些watch表达式的结果是否变化。如果变化，则执行相应的watcher函数。等到model值不再变化，也就不会再有watch函数被触发，则一个digest循环结束。

* $watch: 监听scope model变化
* $apply: 触发“脏检查”
* $digest: 内部函数，执行脏检查。
   digest循环包括2个while循环: 
   * 处理$evalAsync的异步运算队列
   * 处理$watch的wathers队列

![](digest.png)
#####$evalAsync

After a watcher is registered with the scope, the listener fn is called asynchronously (via $evalAsync) to initialize the watcher.

#####$observe和$watch
* $observe: 监听DOM中属性的变化，只能在directive的link函数中使用。
* $watch: 监听scope中属性值的变化

如果directive的DOM上使用{{}}表达式，那么应该用observe。其他大多数情况使用watch。

#####如果都是静态数据，不需要watch，怎么做？
使用**one-time**绑定(Angular 1.3之后引入的)

两种实现方式：
* ```{{::text}}```
* 使用bindonce库:[https://github.com/Pasvaz/bindonce](https://github.com/Pasvaz/bindonce)

