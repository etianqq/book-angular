# Injector

[Studying the Angular JS Injector](http://taoofcode.net/studying-the-angular-injector/)

####instance-Injector
    return {
      invoke: invoke(fn, [self], [locals]),  // return none
      instantiate: instantiate(Type, [locals]),  // return 一个新实例
      get: get(name, [caller]), // return serivce实例
      annotate: annotate(fn, [strictDi]), //return Array: 依赖服务的名字
      has: function(name) {
        return providerCache.hasOwnProperty(name + providerSuffix) || cache.hasOwnProperty(name);
      }
    };
    
 ####annotate
 有3种方法可以annotate函数：
 1. 用数组：```['$scope', '$q', function($scope, $q) {}```
 2. 用```$inject```属性：

  ```function myFunction($scope, $q) {}```
  
  ```myFunction.$inject = ['$scope', '$q'];```
 3. ```function myFunction($scope, $q) {}```注意，在minified模式下不可以工作
    
 