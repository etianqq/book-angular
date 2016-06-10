# AOP机制

####什么是AOP
AOP(Aspect-Oriented Programming)，面向切面编程。

通过compile时植入代码，runtime时动态代理，以及框架提供管道式执行等策略实现程序**通用功能与业务模块的分离**，统一处理，维护的一种**解耦设计**。

AOP是OOP的延续，是函数式编程的一种衍生泛型。

AOP实用场景有：权限控制，日志模块，事务处理，性能统计，异常处理等**独立**，**通用**的**非业务**模块。

下面是Angular中两类常见的AOP切入点。

#####1. http拦截器(管道式策略)

    //定义拦截器
    angular.module('myApp')
      .factory('myInterceptor',
        function($q) {
          var interceptor = {
            'request': function(config) {
                // Successful request method
                return config; // or $q.when(config);
             },
            'response': function(response) {
                // successful response
                return response; // or $q.when(config);
             },
            'requestError': function(rejection) {
                // an error happened on the request if we can recover from the error，
                // we can return a new request or promise
                return response; // or new promise
                // Otherwise, we can reject the next by returning a rejection
                // return $q.reject(rejection);
              },
              'responseError': function(rejection) {
                // an error happened on the request if we can recover from the error,
                // we can return a new response or promise
                return rejection; // or new promise
                // Otherwise, we can reject the next by returning a rejection
                // return $q.reject(rejection);
              }
          };
          return interceptor;
      });

    // 使用拦截器
    angular.module('myApp')
      .config(function($httpProvider) {
          $httpProvider.interceptors.push('myInterceptor');
    });
#####2. 装饰器(运行时动态代理)
用装饰器来修饰一个服务；装饰器在config阶段运行

* 在provider中实现decorator
    angular.module('myApp', [])
      .config([ '$provide', function($provide) {
          $provide.decorator('$log', ['$delegate', function $logDecorator($delegate) {
            var originalWarn = $delegate.warn;
            $delegate.warn = function decoratedWarn(msg) {
                msg = 'Decorated Warn: ' + msg;
                originalWarn.apply($delegate, arguments);
            };
            return $delegate;
        }]);
    }]);
    
* 在module中实现decorator
  
  ```angular.module('myApp').decorator('theFactory', moduleDecoratorFn);``` 