# 嵌套表单

使用ng-form实现嵌套表单

    <form name="userForm" novalidate>
      <div class="form-group" ng-repeat="user in formData.users">
        <ng-form name="userFieldForm">
          <label>{{ user.name }}'s Email</label>
          <input type="text" class="form-control" name="email" ng-model="user.email" required>
          <p class="help-block" ng-show="userFieldForm.email.$invalid">Valid Email Address Required</p>
        </ng-form>
      </div>
    </form>

ngForm可以在主表单中创建独立的子表单，实现**子表单的独立验证**。

Demo: [https://jsfiddle.net/75dbLuut/](https://jsfiddle.net/75dbLuut/)

