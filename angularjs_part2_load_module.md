# 模块加载

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
