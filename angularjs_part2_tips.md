# $parse和$eval

####1.$parse和$eval
相同点：
* 都可以解析/计算Angular表达式的值；
* 支持locals参数，可提供额外的上下文；

不同点：
* $parse：是一个独立的服务，可以在任意地方注入后使用，返回一个函数，需要显性得把执行上下文传给这个函数；
* $eval：是scope对象上的一个API，执行上下文为所在的scope对象；

####2.$observe和$watch
* $observe: 监听DOM中属性的变化，只能在directive的link函数中使用。
* $watch: 监听scope中属性值的变化

如果directive的DOM上使用{{}}表达式，那么应该用observe。其他大多数情况使用watch。

####3.'one-time'绑定
如果都是静态数据，不需要watch，怎么做？
使用**one-time**绑定(Angular 1.3之后引入的)

两种实现方式：
* ```{{::text}}```
* 使用bindonce库:[https://github.com/Pasvaz/bindonce](https://github.com/Pasvaz/bindonce)

####4. $sce服务
“严格情境转义(strict contextual escaping)”服务，对危险的字符串进行检测，使其可以被安全的渲染出来，输出HTML(防止XSS攻击)。

提供的方法有：trustAsHtml, trustAsUrl, trustAsResourceUrl, trustAsJs

####$broadcast,$emit,$on
* $broadcast：在$scope中向下广播事件
* $emit: 在$scope中向上广播事件
* $on: 监听事件


    // firing an event upwards
    $scope.$emit('myCustomEvent', 'Data to send');
    
    // firing an event downwards
    $scope.$broadcast('myCustomEvent', {
        someProp: 'Sending you an Object!' // send whatever you want
    });
    
    // listen for the event in the relevant $scope
    $scope.$on('myCustomEvent', function (event, data) {
        console.log(data); // 'Data to send'
    });



    