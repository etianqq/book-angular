# Injector

[Studying the Angular JS Injector](http://taoofcode.net/studying-the-angular-injector/)

####instance-Injector
    return {
      invoke: invoke(fn, [self], [locals]),
      instantiate: instantiate(Type, [locals]),
      get: get(name, [caller]),
      annotate: annotate(fn, [strictDi]),
      has: function(name) {
        return providerCache.hasOwnProperty(name + providerSuffix) || cache.hasOwnProperty(name);
      }
    };
    
 