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

### 4.核心功能模块

#### 1\).路由

AngularJS路由功能是一个纯前端的解决方案，与我们熟悉的后台路由不太一样。后台路由，通过不同的URL会路由到不同的控制器上\(controller\)，再渲染\(render\)到页面\(HTML\)。AngularJS的前端路由，需求提前对指定的\(ng-app\)，定义路由规则\(routeProvider\)，然后通过不同的URL，告诉\(ng-app\)加载哪个页面\(HTML\)，再渲染到\(ng-app\)视图\(ng-view\)中。

AngularJS的前端路由，虽然URL输入不一样，页面展示不一样，其实完成的单页\(ng-app\)视图\(ng-view\)的局部刷新。这样来看，AngularJS做单页应用就有点标配的感觉了。

无刷新的视图切换。

#### 2\).Filter

过滤器用来格式化表达式中的值。过滤器可以使用一个管道字符（\|）添加到表达式和指令中。

#### 3\).指令

指令就是一些附加在HTML元素上的自定义标记（例如：属性，元素，或css类），它告诉AngularJS的**HTML编译器**\([`$compile`](http://www.angularjs.net.cn/tutorial/api/ng.$compile)\) 在元素上附加某些指定的行为，甚至操作DOM、改变DOM元素，以及它的各级子节点。

Angular内置了一整套指令，如`ngBind`,`ngModel`, 和`ngView`。 就像你可以创建控制器和服务那样，你也可以创建自己的指令来让Angular使用。 当Angular[启动器](http://www.angularjs.net.cn/tutorial/guide/bootstrap)引导你的应用程序时，[HTML编译器](http://www.angularjs.net.cn/tutorial/guide/compiler)就会遍历整个DOM，以匹配DOM元素里的指令。

#### 4\).服务

存放持久性的数据，存放实现某些特定功能方法的类库\(自定义方法，第三方类库\)，依赖注入

#### 5\).控制器

控制器构造函数仅在AngularJS对HTML文档进行编译时被执行一次。

通常情况下，控制器不应被赋予太多的责任和义务，它只需要负责一个单一视图所需的业务逻辑。

在angularJS中，controlle是一个javascript函数/类，用于操作作用域中，各个对象的初始状态以及相应的行为。

控制器在Angularjs中的作用是增强视图，它实际就是一个函数，用来向视图中的作用域添加额外的功能，我们用它来给作用域对象设置初始状态，并添加自定义行为。

控制器之间通过“广播”进行通信。

# 二.项目开始与架构

### 1.AngularJS项目架构目录

### 2.AngularJS项目起步



