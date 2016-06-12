# 表单(form)

####表单元素
* 基于文本的输入: text, textarea, e-mail, URL, number
* 其他: checkbox, radio, select(ng-options)

####ngModelController

![](ngModel.jpg)

ngModelController负责管理存储在模型(ngModel)中的值与Input元素显示值之间的数据绑定。

####model和view之间的值转换
![](ngModel2.png)

####validation
每一个form指令都会创建一个**ngFormController**的实例。

ngFormController对象管理表单的valid/invalid/pristine/dirty...状态，并与ngModelController协同工作跟踪表单中的每个ngModel字段。


