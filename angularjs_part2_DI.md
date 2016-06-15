# 依赖注入-DI
DI-dependency injection

* “需要哪个对象，就可以得到哪个对象！” 

* Angular在每个module上都有一个注册表，里面对象名称和相应的callback function。

* 被注入的对象都是单例对象

* 只有下面的函数可以使用依赖注入(通过module注册的函数都可以)

```controller, service/factory/provider, directive, filter, animation, config, run, decorator```
![](injector2.png)

官网文档：[Dependency Injection](https://docs.angularjs.org/guide/di)