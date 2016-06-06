# 过滤器(filter)

* 用来格式化需要显示给用户的数据。
* 有内置过滤器和自定义过滤器
 
例子：

1. 使用表达式：```{{ name | uppercase }}```
2. 使用$filter来调用过滤器：

        app.controller('DemoController', ['$scope', '$filter',
          function($scope, $filter) {
            $scope.name = $filter('lowercase')('Ari');
        }])