# 模块加载

Angularjs模块可以在被加载和执行前对其自身进行配置。

####1. 配置块(config block)
仅仅只有providers和constants可以被注入到配置块中

    angular.module('myApp', [])
      .config(function($provide) { ...})
实际上，基于provider，有很多config的语法糖，如下例：

    angular.module('myModule', []).
      value('a', 123).
      factory('a', function() { return 123; }).
      directive('directiveName', ...).
      filter('filterName', ...);

    // Angular在编译时会执行这些函数，is same as
    
    angular.module('myModule', []).
      config(function($provide, $compileProvider, $filterProvider) {
        $provide.value('a', 123);
        $provide.factory('a', function() { return 123; });
        $compileProvider.directive('directiveName', ...);
        $filterProvider.register('filterName', ...);
    });
####2. 运行块(run block)
在injector创建之后被执行，是Angular应用中第一个被执行的方法。

* 类似main方法
* 因为与应用本身耦合度高所以难以单元测试
* 通常用来注册全局的事件监听器，配置服务/$rootScope/时间...

例子：每次路由变化时，需要执行一个函数来验证用户权限

    angular.module('myApp', [])
      .run(function($rootScope, AuthService) { 
         $rootScope.$on('$routeChangeStart', function(evt, next, current) {
            // If the user is NOT logged in
            if (!AuthService.userLoggedIn()) {
                if (next.templateUrl === "login.html") {
                // Already heading to the login route so no need to redirect
                } else { $location.path('/login');}
            }
          });
      });