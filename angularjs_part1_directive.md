# 指令(directive)

分为内置指令和自定义指令。

按照使用场景和作用可以分为2类：功能型指令和装饰器型指令

####内置指令
内置指令以ng-XXX命名。


####自定义指令

    angular.module('app', []).directive('myDirective', function() {
      return {
          restrict: String,               
          priority: Number,
          terminal: Boolean,
          template: String or Template function(tElement, tAttrs) {...},
          templateUrl: String,
          replace: Boolean or String,
          scope: Boolean or Object,
          transclude: Boolean,
          controller: String or function(scope, element, attrs, transclude, otherInjectables) { ... },
          controllerAs: String,
          require: String,
          link: function(scope, iElement, iAttrs) { ... },
          compile: // 返回一个对象或连接函数，如下所示：
              function(tElement, tAttrs, transclude) {
                  return {
                      pre: function(scope, iElement, iAttrs, controller) { ... },
                      post: function(scope, iElement, iAttrs, controller) { ... }
                   }
                  // 或者     
                  return function postLink(...) { ... }
              }
        };
     });

#####自定义指令的scope
scope: false/true/@/=/&
* false：共享父作用域
* ture: 继承父作用域，且创建独立作用域
* 对象{}: 不继承父作用域，且创建独立作用域

