# Injector

使用apply实现依赖注入

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
 
    // inferred (only works if code not minified/obfuscated)
    $injector.invoke(function(serviceA){});

    // annotated
    function explicit(serviceA) {};
    explicit.$inject = ['serviceA'];
    $injector.invoke(explicit);

    // inline
    $injector.invoke(['serviceA', function(serviceA){}]);

####instantiate
在构造函数中使用$injector

      function instantiate(Type, locals) {
        var Constructor = function() {},instance, returnedValue;

        // Check if Type is annotated and use just the given function at n-1 as parameter
        Constructor.prototype = (isArray(Type) ? Type[Type.length - 1] : Type).prototype;
        instance = new Constructor();
        returnedValue = invoke(Type, instance, locals);

        return isObject(returnedValue) || isFunction(returnedValue) ? returnedValue : instance;
    }
    
源码分析：[Studying the Angular JS Injector](http://taoofcode.net/studying-the-angular-injector/)
    
 