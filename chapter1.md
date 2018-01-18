# Chapter 4:模块

## Section 4.1:模块

模块是作为App不同功能部分的一个容器，例如控制器，服务，过滤器，指令等。

模块可以通过Angular的依赖注入机制被其他模块所引用。

### Create a module:

`angular.module(app,[]);`

上述例子中数组\[ \]里是App所依赖的模块的集合，如果app没有任何依赖，那我们就使用空的数组，如\[ \].

### Injecting\(注入\) a module as a dependence of another module:

`angular.module('app',['app.auth','app.dashboard']);`

### Referencing a module:

```
angular.module('app');
```

## Section 4.2:

### Why to use Modules

大多数应用都有一个主函数将应用的不同部分进行捆绑，实例化。

Angular应用没有主函数。

但是在AngularJS中声明的过程是易于理解的，并且可以将代码打包成可复用的模块。

模块可以在任意顺序下被加载，因为模块是延迟执行的。

### Declare a module

```
var app = angular.module('app',[]);
//Empty array is list of modules app is depends on
//if there are ang required dependancies,
//then you can add in module,like['ngAnimate']

app.controller('myCtrl',function(){
    //write you bussiness logic here
})
```

### Module Loading and Dependencies

1.配置代码块：在Provider和配置阶段执行

```
angular.module('myModule',[])
    .config(function(){
    })
```



