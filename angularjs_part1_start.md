# Angularjs启动过程
![](angular-start.jpg)

1. 浏览器下载HTML/CSS/Javascript
2. 浏览器构建DOM tree
3. JQuery初始化(挂上DOMContentLoaded)

    如果Angular自己哦亲引入JQuery，则Angular会使用JQurey API;否则，启用内置的jQLite。
4. Angular初始化

  * 按照名字创建模块
  * 在模块中测试各类Angular对象，如Controller,Service,Directive...
  * 注册之后，生产一个map={name:callback}
  * 模块中注册的config callback，会执行！
  
5. JQuery启动(浏览器触发DOMContentLoaded事件，执行callback)
6. Angular启动
  * 自动启动(```ng-app="myApp"```)或手动启动(```angular.bootstrap(document, ['myApp']);```)
7.
