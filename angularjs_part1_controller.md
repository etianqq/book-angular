# 控制器(controller)
* 是一个函数，用来向视图的作用域中添加额外的功能。
* 初始化数据，定义事件，等等

      <div ng-controller="FirstController">
        <button ng-click="add(1)" class="button">Add</button>
        <h4>Current count: {{ counter }}</h4>
      </div>
      -----------------------------------------------------------------
      app.controller('FirstController', function($scope) {
        $scope.counter = 0;
        $scope.add = function(amount) { $scope.counter += amount; };
      });
      
####Controller as vm
* 不在controller里面注入$scope，而是将其一个普通的JS对象使用。
* 该contoller实例会成为$scope的一个属性，于是，该对应的视图模板上所有字段都会限制在一个别名引用属性上。

      <div ng-controller="MyController as vm">
        <span>{{vm.message}}</span>
        <button ng-click="vm.onClick()">Click Me</button>
      </div>
      -----------------------------------------------------------------
      app.controller('MyController', function() {
        var vm = this;
        vm.message = 'You have not clicked anything yet.';
        vm.onClick = function() {
            ctl.message = 'You clicked something.';
          };
        return vm;  
      });