# jpype1


## 基础介绍

JPype（全称 Java-Python Extension）是一个 在 Python 中直接调用 Java 代码的库
- 在同一个进程里启动 Java 虚拟机（JVM）
- 让 Python 程序像使用普通模块一样 调用 Java 类和方法
- 实现 Java 与 Python 的无缝互操作


JPype实现原理：
- JPype 用 JNI（Java Native Interface） 把 Python 解释器和 JVM 连接起来
- 当 import 一个 Java 包时，JPype 会在 JVM 中加载对应的类，并在 Python 中创建一个“代理对象”
- 这个代理对象的调用会直接映射到 Java 方法调用


## 核心内容
```yaml
jpype:
    imports:
    JClass: # 加载Java类
    JString:
    @JImplements:
    @JOverride:
    getDefaultJVMPath():
    isJVMStarted():
    shutdownJVM():
    startJVM(): # 启动JVM
        classpath:
```