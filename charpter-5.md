# Charpter 5: Components\(组件\)

| Parameter | Details |
| :--- | :--- |
| = | 双向数据绑定。 |
| &lt; | 单向数据绑定。 |
| @ | 字符参数 |
| & | 当组件需要向父作用域传递信息时作为回调函数 |
| LifeCyle Hooks | Details |
| $onInit | 在一个元素上所有控制器被构造完成后，遍历每一个控制器，初始化其中的绑定数据。适合存放控制器的赋值代码 |
| $onChanges\(changesObj\) | 在单项绑定数据\(父组件向子组件传递的数据\)更新时调用。changesObj是一个哈希表，其关键字是属性值被改变的属性的名字，值是一个数组，格式为{currentValue,previousValue,isFirstChange\(\)} |
| $onDestory\(\) | 在一个控制的作用域被销毁是调用。利用此钩子函数，释放外部资源，监视器以及事件处理器。 |
| $postLink\(\) | 在一个元素与其子元素被link后调用，这个钩子函数与Angular 2中的ngAfterViewInit 和ngAfterContentInit 钩子函数 类似 |
| $doCheck\(\) | 在每一次digest circle 时调用。提供了对changes进行监测并实施行为的机会。任何你希望对changes进行相应的行为都需要在此钩子函数中进行唤醒，并且在$onChanges被调用的时候，调用此函数没有任何作用！ |

## Section 5.1:Basic Components and LifeCycle Hooks

### What is a component?

* 组件是基础化的指令，但是配置更简单，并适合组件化的架构（Angular2的精髓）。我们可以把组件看作是一个微件（widget）：可以在web应用不同地方复用的代码块。

### Component

```
angular.module('myApp',[])
    .component('helloWorld',{
        template:'<span>Hello World!</span>'
    })
```

### Make up

```
<div ng-app='myApp'>
    <hello-world></hello world>
</div>
```

### Using External data in component:

我们可以添加一个参数，给我们的组件传递一个name，使用方法如下：

```
angular.module('myApp',[])
    .component("helloWorld",{
        template:'<span>Hello {{$ctrl.name}}</span>',
        bindings:{name:'@'}
    })
```

### Make up

```
<div ng-app='myApp'>
    <hello-world name='Jhon'></hello-world>
</div>
```

### Using controllers in components

让我们看一下如果添加控制器

```
angular.module('myApp',[])
    .component('helloWorld',{
        template:'<span>Hello {{$ctrl.name}},I'm {{$ctrl.myName}}!</span>'
        bindings:{name:'@'},
        controller:function(){
            this.myName="Nebulas";
        }
    })
```

传递给组件的参数可以在控制器的$onInit函数调用时在控制器的作用域中获取到。例如：

```
angular.module("myApp",[])
    .component('helloWorld',{
        template:'Hello {{$ctrl.name}},I'm {{$ctrl.myName}}',
        bindings:{name:'@'},
        controlller:function(){
            this.$onInit=function(){
                this.myName='Mac'+this.name;
            }

        }
    })
```

在以上的组件中，页面将渲染出“Hello John,I'm MacJhon”.

> 要注意的是$ctrl是controllerAs的默认值，如果实现没有指定的话

### Using "require" as an Object

在某些情况下，你也许需要从某些父组件中获取数据到你的组件中。

我们可以通过声明该组件require某父组件来实现，require让我们可以引用被需求模块的控制器中的数据，并在我们的控制器中使用，如下所示：

> 要注意的是，被require的controller仅仅在$onInit钩子函数声明后有保证地准备好

```
angular.module('myApp',[])
    .component('helloWorld',{
        template:"<span>Hello {{$ctrl.name}},I'm {{$ctrl.myName}}</span>",
        bindings:{name:'@'},
        require:{
            parent:'^parentComponent'
        },
        controller:function(){
            //here this.parent might not be initiated yet
            this.$onInit=function(){
                //after $onInit,use this.parent to access required controller
                this.parent.foo();
            }
        }
    })
```



















