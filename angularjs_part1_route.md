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
      config(['$routeProvider', function($routeProvider) {
        $routeProvider
          .when('/', {
            templateUrl: 'views/home.html',
            controller: 'HomeController'
          })
          .when('/login', {
            templateUrl: 'views/login.html',
            controller: 'LoginController'
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
    }]);