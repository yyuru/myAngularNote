# Chapter 4:模块

## Section 4.1:模块

模块是作为App不同功能部分的一个容器，例如控制器，服务，过滤器，指令等。

模块可以通过Angular的依赖注入机制被其他模块所引用。

### Create a module:

`angular.module(app,[]); `

上述例子中数组\[ \]里是App所依赖的模块的集合，如果app没有任何依赖，那我们就使用空的数组，如\[ \].

### Injecting\(注入\) a module as a dependence of another module:

`angular.module('app',['app.auth','app.dashboard']);`





