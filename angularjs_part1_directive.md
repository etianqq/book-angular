# 指令(directive)

分为内置指令和自定义指令。
####内置指令
内置指令大多是以ng-XXX命名。

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


