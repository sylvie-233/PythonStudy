# Python


## 基础介绍





## 核心内容

```yaml
std:
    ast: 抽象语法树
        parse():
```


### 面向对象

Class为type类型的对象实例，基类为object

object为type类型的对象实例，没有基类

type为type自身类型的对象实例，基类为object

（type是type，object也是type；type继承自object，object没有继承；Class是type，继承自object）

`class = type(classname, superclass, attributedict)`

- type为对象的顶点，所有对象都创建自type。
- object为类继承的顶点，所有类都继承自object。



#### metaclass

metaclass影响类本身的创建行为

metaclass继承自type

一旦把自定义类类型 MyClass 的 metaclass 设置成 MyMeta，MyClass 就不再由原生的 ty

类对象创建`__call__() -> __new__() -> __init__()` 
