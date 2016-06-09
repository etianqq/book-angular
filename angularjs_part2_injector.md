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
 
    // inferred (only works if code not minified/obfuscated)
    $injector.invoke(function(serviceA){});

    // annotated
    function explicit(serviceA) {};
    explicit.$inject = ['serviceA'];
    $injector.invoke(explicit);

    // inline
    $injector.invoke(['serviceA', function(serviceA){}]);

####invoke

    
 