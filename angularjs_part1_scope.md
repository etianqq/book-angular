# 作用域(scope)

* $scope对象在Angularjs中充当数据模型/视图模型(view model)。

* 使用了原型继承的方式，下级的scope可以读取上级scope的属性。

* 最顶级的scope是$rootScope。 

例子：

      <div ng-app="myApp">
      <h1>Hello {{ name }}</h1>
      </div>

      angular.module('myApp', [])
        .run(function($rootScope) {
          $rootScope.name = "World";
      });
      
####scope的生命周期
1. **创建**：创建controller/directive时，会创建一个新的scope
2. **链接**：Angular运行时，会将scope对象link到视图中
3. **更新**：在$digest cycle时(执行在$rootScope上)，所有的子scope会执行dirty digest checking。如果有任意变化，会触发scope回调函数
4. **销毁**：当一个scope不在需要，在scope会调用$destory()清理和销毁自己