# pytest

``

## 基础介绍

python 测试库

- 基于 Python 标准 assert 的增强语法
- 自动发现测试用例
- 简单易用、模块化、可扩展的 fixtures
- pytest 有非常强大的插件，并且这些插件能够实现很多的实用的操作

文件：`test_*.py`或者`*_test.py`
类：`Test*`
方法：`test_*()`


- 支持依赖注入fixture
- mark、fixture、conftest
- function、class、module、session

### pytest
```yaml
pytest:
    -k: # 执行名称匹配的测试
    -m: # 执行指定标记mark的测试
    -n: # 多进程执行
    -p: # 启用插件
        html:
    -r:
        f:
    -s: # 支持控制台输入、输出
    -v: # 显示详细的测试结果
    -x: # 失败快速退出
    --ff: # 先运行上次失败的测试，再运行其他测试
    --lf: # 只运行上次失败的测试
    --html:
    --markers: # 查看标记
    --maxfail:
    --pyargs:
    --version: # 版本信息
```

#### pytest.ini
```yaml
pytest.ini:
    addopts: 
    pytest:
        norecursedirs:
        testpaths:
    markers: # 自定义标记
```


#### pyproject.toml
```yaml
pyproject.toml:

```

#### settings.json
```yaml
settings.json:
    python.testing.pytestEnabled: # true,
    python.testing.unittestEnabled: # false,
    python.testing.nosetestsEnabled: # false,
    python.testing.pytestArgs: # tests
    python.analysis.extraPaths: # src
    terminal.integrated.env.windows: # PYTHONPATH: ${workspaceFolder}/src
```



## 核心内容
```yaml
pytest:
    mark: # 测试标记
        @flaky: # 自动重试
            reruns:
            reruns_delay:
        @parametrize: # 参数化测试（参数名、数据）
        @skip: # 测试跳过
            reason: # 跳过理由
        @skipif:
        @xfail: # 抛出异常检测
    @fixture:
        autouse: # 自动使用
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


### mark

pytest标记
支持自定义标记


#### skip
#### skipif
#### xfail
#### parametrize
#### flaky
#### usefixtures

### fixtures

提供测试依赖的机制
实现依赖注入、同名参数

yield实现测试前置后置钩子（依赖顺序、参数顺序）


scope作用域：
- function：每个测试函数前后（默认）
- class：每个测试类前后
- module：每个测试文件前后
- session：整个测试运行前后


#### conftest.py

`conftest.py`

测试配置、fixtures定义共享
每个目录支持一个，支持多层嵌套




### plugin

插件核心功能：
1. fixture 提供静态依赖，
2. pytest_addoption 提供外部输入，
3. pytest_generate_tests 提供动态参数化

- pytest_generate_tests(metafunc)：参数化动态生成测试参数
- pytest_fixture_setup(fixturedef, request)：在 fixture 初始化前做额外控制
- pytest_addoption(parser)：添加命令行参数（并通过 fixture 注入）
- pytest_configure(config)：注册全局行为或状态

pytest插件扩展参数函数


#### pytest-html
#### pytest-rerunfailures
#### pytest-result-log
#### pytest-selenium
#### pytest-xdist 
#### allure-pytest 



## pytest原理

```
FixtureManager
   ├── registry: 所有 fixture 定义
   ├── hookproxy: 所有插件钩子
   └── resolver: 参数解析器
```
参数注入流程：
1. pytest 收集所有测试函数；
2. 解析每个参数名；
3. 在 FixtureManager.registry 中查找同名 fixture；
4. 若找不到，调用钩子 pytest_generate_tests；
5. fixture 解析器递归分析依赖并执行；
6. 将结果注入测试函数