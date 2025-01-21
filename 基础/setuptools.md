# setuptools

## 基础介绍


二进制包：`.egg`、`.whl`








### setup.py
```yaml
setup.py:
    --formats: # 压缩格式
    bdist: # 二进制打包（）
        bdist_egg:
        bdist_wheel:
    build:
    build_ext:
    check: # 配置错误检查
    clean:
    install: # 打包、安装（本地仓库）
    sdist: # 生成dist目录（.tar.gz、.egg-info）
    upload:
```

打包主配置文件



### MANIFEST.in
```yaml
MANIFEST.in:
    include:
    recursive-include: # 递归包含文件
```


## 核心内容
```yaml
setuptools:
    command:
        build_ext:
    Extension: # python扩展类
        name:
        sources:
        include_dirs:
    find_packages(): # 递归寻找子目录（packages）
    setup(): # 构建主函数
        author: # 作者
        author_email: # 作者邮箱
        classifiers:
        cmdclass:
        description:
        entry_points: # python文件中的函数自动生成为可执行脚本
            console_scripts:
        exclude_package_data: # 去除打包文件
        ext_modules: # 扩展编译
        include_package_data:
        install_requires: # 安装依赖
        keywords:
        license:
        long_description:
        long_description_content_type:
        name: # 模块名
        packages: # 指定源码目录
        package_data: # 指定打包文件
        python_requires: # python版本限定
        scripts: # 把.sh、.py等可执行脚本生成到系统path中
        setup_requires: # setup本身依赖
        tests_require: # 测试依赖
        url:
        version:


wheel: # 构建whl二进制包

```