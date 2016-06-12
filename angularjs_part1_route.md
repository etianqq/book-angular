# 路由(route)

从1.2版本起，路由ngRoute成为单独的模块发布，所以需要先安装ngRoute才能使用：[https://docs.angularjs.org/api/ngRoute](https://docs.angularjs.org/api/ngRoute)

####使用ngRoute
HTML如下：

    <script src="path/to/angular.js"></script>
    <script src="path/to/angular-route.js"></script>
    
在模块中加载ngRoute

    angular.module('app', ['ngRoute']);
    
定义路由

    angular.module('myApp', []).
      // 配置路由
      config(['$routeProvider', function($routeProvider) {
        $routeProvider
          .when('/', {
            templateUrl: 'views/home.html',
            controller: 'HomeController'
          })
          .when('/inbox/:name', {
            templateUrl: 'views/inbox.html',
            controller: 'InboxController'
          })
          .when('/dashboard', {
            templateUrl: 'views/dashboard.html',
            controller: 'DashboardController',
            resolve: {
              user: function(SessionService) {
                return SessionService.getCurrentUser();
                }
            }
          })
          .otherwise({
            redirectTo: '/'
          });
    }])
    // 监听路由变化
    .run(['$rootScope', '$location', function($rootScope, $location) {
        // 路由事件: $routeChangeStart/$routeChangeSuccess/$routeChangeError
        $rootScope.$on('$routeChangeStart', function(evt, next, current) {...})
    }])
    // 使用路由里的$routeParams
    .controller('InboxController', function($scope, $routeParams){
      console.log($routeParams.name);
    })
    // 使用路由resolve中定义的对象
    .controller('DashboardController', function($scope, $routeParams, user){
      // 可以使用user obj
    });