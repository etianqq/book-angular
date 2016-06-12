# 嵌套表单

使用ng-form实现嵌套表单

      <form name="userForm" novalidate>

    <div class="form-group" ng-repeat="user in formData.users">
      <label>{{ user.name }}'s Email</label>
      <input type="text" class="form-control" name="email" ng-model="user.email" required>
      <p class="help-block" ng-show="userForm.email.$invalid">Valid Email Address Required</p>
    </div>

  </form>

