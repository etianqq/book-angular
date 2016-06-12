# XHR

####使用$http

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