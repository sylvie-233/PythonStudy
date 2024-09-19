# setuptools

## 基础介绍


二进制包：`.egg`、`.whl`

### setup.py
```yaml
setup.py:
    --formats: # 压缩格式
    bdist:
    build:
    build_ext:
    clean:
    install:
    sdist:
    upload:
```

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
    find_packages(): # 递归寻找子目录
    setup(): # 构建主函数
        author:
        author_email:
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
        name:
        packages: # 指定源码目录
        package_data: # 指定打包文件
        python_requires: # python版本限定
        scripts: # 把.sh、.py等可执行脚本生成到系统path中
        setup_requires: # setup本身依赖
        tests_require: # 测试依赖
        url:
        version:


wheel:

```