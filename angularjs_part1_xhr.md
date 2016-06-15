# XHR

####使用$http(内置)

    $http({
      method: 'GET',
      url: '/api/users.json'
    }).success(function(data, status, headers, config) {
        // This is called when the response is
        // ready
    }).error(function(data, status, headers, config) {
        // This is called when the response
        // comes back with an error status
    });
    
####使用$resource
支持标准restful数据模型 

####使用Restangular
封装性更好，功能更强大