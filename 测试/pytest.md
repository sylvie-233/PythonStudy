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
    -k: # 执行名称匹配的测试
    -m: # 执行指定标记mark的测试
    -n:
    -r:
        f:
        s:
    -v: # 显示详细的测试结果
    -x:
    --ff: # 先运行上次失败的测试，再运行其他测试
    --lf: # 只运行上次失败的测试
    --maxfail:
    --pyargs:
    --version: # 版本信息
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
    mark: # 测试标记
        @flaky: # 自动重试
            reruns:
            reruns_delay:
        @parametrize: # 参数化测试
        @skip: # 测试跳过
            reason:
        @skipif:
        @xfail: # 抛出异常检测
    @fixture:
        autouse:
        scope:
            package:
            module:
            class:
            function:
            session:
    main(): # 直接执行
    raises(): # 异常捕获上下文测试
    skip():
```


### fixtures

提供测试依赖的机制
实现依赖注入、同名参数

yield实现测试前置后置钩子


#### conftest.py

`conftest.py`

测试配置、fixtures定义共享
