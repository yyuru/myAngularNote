


# AngularJS介绍与项目架构

## 一.概述

### 1.起源

AngularJS诞生于2009年，由Misko Hevery 等人创建，后为Google所收购。目前最新版1.7

### 2.AngularJS与Angular的区别

AngularJS:前端框架。

Angular:基于**TypeScript**的用于构建Web应用的**开发平台。**

### 3.核心特性

#### 1\).MVVM

![](/assets/mvvm.png)

#### 2\).模块化
#### 3\).依赖注入

依赖注入（Dependency Injection，DI）是一种软件设计模式，在这种模式下，一个或更多的依赖（或服务）被注入（或者通过引用传递）到一个独立的对象中，然后成为了该对象的一部分。

AngularJS注入方式：

数组注入

```
var myapp=angular.module('app',["依赖的模块"]);
```

$inject属性注入:

```
myapp.$inject=["依赖的模块"];
```

#### 4\).双向数据绑定

在AngularJS中，数据绑定就是数据模型与视图组件的自动同步，当模型改变时，视图就能反映这种改变，反之亦然。

**实现原理：**

当视图改变了某个值，数据模型会通过脏检查监听到这个变化；反之，视图会依据数据模型的变化重新渲染。

1.在数据模型通过表达式{{aModel}}引入到视图中时，angularjs会给该模型添加一条watcher

2.当我们通过某个事件更改了模型中的一条数据，AngularJS就回自动的调用$digest\(\)出发脏值检查循环，其会触发每一条watcher

3.watcher会对模型进行检测，如果模型发生了变化关联到该watcher的回调函数就会被调用来更新view

### 4.核心功能模块

#### 1\).路由

AngularJS路由功能是一个纯前端的解决方案，需要提前对指定的\(ng-app\)，定义路由规则\(routeProvider\)，然后通过不同的URL，告诉\(ng-app\)加载哪个页面\(HTML\)，再渲染到\(ng-app\)视图\(ng-view\)中，实现无刷新的视图切换。

#### 2\).Filter

过滤器用来格式化表达式中的值。过滤器可以使用一个管道字符（\|）添加到表达式和指令中。


```
<div ng-app="myApp" ng-controller="personCtrl">

<p>姓名为 {{ lastName | uppercase }}</p>

</div>

```


#### 3\).指令

指令就是一些附加在HTML元素上的自定义标记（属性，元素，或类名），它告诉AngularJS的**HTML编译器**\在元素上附加某些指定的行为，甚至操作DOM、改变DOM元素，以及它的各级子节点。

#### 4\).服务

存放持久性的数据，存放实现某些特定功能方法的类库\(自定义方法，第三方类库\)，依赖注入

#### 5\).控制器


控制器在Angularjs中的作用是增强视图，它实际就是一个函数，用来向视图中的作用域添加额外的功能，我们用它来给作用域对象设置初始状态，并添加自定义行为。
通常情况下，控制器只需要负责一个单一视图所需的业务逻辑。
控制器之间通过“广播”进行通信。


```
var myApp=angular.module('myApp',[]);
myApp.controller("myController",[$scope,function($scope){
    //操作$scope
}])
```



# 二.项目开始与架构

### 1.AngularJS项目架构目录
app/  &nbsp;&nbsp;&nbsp;&nbsp; ->根目录
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;assets/&nbsp;&nbsp;&nbsp;&nbsp;->静态文件
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;css/&nbsp;&nbsp;&nbsp;&nbsp;->css文件
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;img/&nbsp;&nbsp;&nbsp;&nbsp;->图片文件
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;lib/&nbsp;&nbsp;&nbsp;&nbsp;->库文件
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;angular/&nbsp;&nbsp;&nbsp;&nbsp;->angularjs库文件
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;js/&nbsp;&nbsp;&nbsp;&nbsp;->脚本文件
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;app.js&nbsp;&nbsp;&nbsp;&nbsp;->应用的main脚本
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;service.js&nbsp;&nbsp;&nbsp;&nbsp;->自定义服务
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;filter.js&nbsp;&nbsp;&nbsp;&nbsp;->自定义filter
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;directive.js&nbsp;&nbsp;&nbsp;&nbsp;->自定义指令
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;views/&nbsp;&nbsp;&nbsp;&nbsp;->视图文件
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;view1/&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;view1.html&nbsp;&nbsp;&nbsp;&nbsp;->视图页面
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;view1Controller.js&nbsp;&nbsp;&nbsp;&nbsp;->视图控制器
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;view2/&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;view2.html&nbsp;&nbsp;&nbsp;&nbsp;->视图页面
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;view2Controller.js&nbsp;&nbsp;&nbsp;&nbsp;->视图控制器
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;index.html&nbsp;&nbsp;&nbsp;&nbsp;->应用入口

### 2.AngularJS项目起步

1).引入angular.js

