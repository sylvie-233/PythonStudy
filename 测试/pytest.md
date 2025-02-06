# pytest

## 基础介绍

python 测试库

- 基于 Python 标准 assert 的增强语法
- 自动发现测试用例
- 简单易用、模块化、可扩展的 fixtures
- pytest 有非常强大的插件，并且这些插件能够实现很多的实用的操作

文件：`test_*.py`或者`*_test.py`
类：`Test*`
方法：`test_*()`


支持依赖注入

### pytest
```yaml
pytest:
    -k:
    -n:
    -r:
        f:
        s:
    -x:
    --maxfail:
    --pyargs:
    --version:
```

#### pytest.ini
```yaml
pytest.ini:
    pytest:
        norecursedirs:
        testpaths:
```



## 核心内容
```yaml
pytest:
    mark:
        @flaky(): # 自动重试
            reruns:
            reruns_delay:
        @parametrize():
        @skip():
            reason:
        @skipif():
        @xfail(): # 抛出异常检测
    @fixture():
        autouse:
        scope:
            package:
            module:
            class:
            function:
            session:
    main(): # 直接执行
    raises():
    skip():
```


### fixtures

实现依赖注入、同名参数

yield实现测试前置后置钩子


#### conftest

`conftest.py`

测试配置、fixtures定义共享
