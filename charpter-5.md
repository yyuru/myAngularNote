# Charpter 5: Components\(组件\)

| Parameter | Details |
| :--- | :--- |
| = | 双向数据绑定。 |
| &lt; | 单向数据绑定。 |
| @ | 字符参数 |
| & | 当组件需要向父作用域传递信息时作为回调函数 |
| LifeCyle Hooks | Details |
| $onInit | 在一个元素上所有控制器被构造完成后，遍历每一个控制器，初始化其中的绑定数据。适合存放控制器的赋值代码 |
| $onChanges\(changesObj\) | 在单项绑定数据更新是调用。changesObj是一个哈希表，其关键字是属性值被改变的属性的名字，值是一个数组，格式为{currentValue,previousValue,isFirstChange\(\)} |
| $onDestory\(\) |  |
| $postLink\(\) |  |
| $doCheck\(\) |  |



