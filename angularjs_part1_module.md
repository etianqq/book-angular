# 模块(module)
模块：把相关的一组编程元素组织到一个发布包中，这些编程元素之间紧密协作，隐藏细节，只通过公开的接口与其他模块合作。


####声明模块
```angular.module('myApp', []);```

####调用模块
```angular.module('myApp')```

####模块加载
Angularjs模块可以在被加载和执行前对其自身进行配置。

#####1. 配置
可在应用启动前进行修改

    angular.module('myApp', [])
      .config(function($provide) { ...})
      .provider('myProvider', function () {...});
      
| Provider | Singleton | Instantiable | Configurable |
| -- | -- | -- | -- |
| Constant | Yes | No | No |
| Value | Yes | No | No |
| Service | Yes | No | No |
| Factory | Yes | Yes | No |
| Provider | Yes | Yes | No |
