# 脏检查机制

Angular将双向绑定转换为一堆watch表达式，然后递归检查这些watch表达式的结果是否变化。如果变化，则执行相应的watcher函数。等到model值不再变化，也就不会再有watch函数被触发，则一个digest循环结束。

