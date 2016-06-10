# 模块加载

Angularjs模块可以在被加载和执行前对其自身进行配置。

#####1. 配置-config
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
