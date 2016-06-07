# Angular启动过程
![](angular-start.jpg)

1. 浏览器下载HTML/CSS/Javascript
2. 浏览器构建DOM tree

3. JQuery初始化(挂上DOMContentLoaded)
  * 如果在Angular脚本之前引入JQuery，则Angular会使用JQurey API;否则，启用内置的jQLite。
4. Angular初始化
  * 按照名字创建模块
  * 在模块中测试各类Angular对象，如Controller,Service,Directive...
  * 注册之后，生产一个map={ojbName:callback}
  
5. JQuery启动(浏览器触发DOMContentLoaded事件，执行callback)
6. Angular启动
  * 自动启动(```ng-app="myApp"```)或手动启动(```angular.bootstrap(document, ['myApp']);```)
  
7. **加载**子模块
  * 创建注入器(injector)，把它关联到DOM节点上(样之前注册好的那些Angular对象才能被使用)
  * 模块中注册的config callback，会执行！(config callback只能使用Constant对象和Provider类)

8. **启动**子模块
  * 模块加载完会执行所有"run callback"，这时，Angular对象可用。
  * Route module获得控制权

9. 渲染页面
  * 创建$scope，加载模板
  * $compile通过指令将$scope和DOM tree关联起来

10. 数据绑定和$digest/$apply