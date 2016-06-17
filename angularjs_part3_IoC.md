# 控制反转

"控制反转"（Inversion of Control）的一个著名的同义原则是由Robert C. Martin提出的"依赖倒置原则"(Dependency Inversion Principle)。

所以，"控制反转"=="依赖倒置原则"。

####依赖倒置
* High level modules should not depend upon low level modules. 
* Both should depend upon abstractions. 
* Abstractions should not depend upon details. Details should depend upon abstractions。

翻译过来，包含三层含义：

* 高层模块不应该依赖低层模块，两者都应该依赖其抽象;
* 抽象不应该依赖细节;
* 细节应该依赖抽象;

在Java语言中，抽象就是指接口或抽象类，两者都是不能直接被实例化的；细节就是实现类，实现接口或继承抽象类而产生的类就是细节，其特点就是可以直接被实例化，也就是可以加上一个关键字new产生一个对象。依赖倒置原则在Java语言中的表现就是：

* 模块间的依赖是通过抽象发生，实现类之间不发生直接的依赖关系，其依赖关系是通过接口或抽象类产生的；
* 接口或抽象类不依赖于实现类；
* 实现类依赖接口或抽象类。
     
更加精简的定义就是“面向接口编程”——OOD（Object-Oriented Design，面向对象设计）的精髓之一。