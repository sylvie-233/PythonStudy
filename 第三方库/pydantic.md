# Pydantic


## 基础介绍


数据校验库、提供模型的序列化和反序列化
- 基于 Python 类型提示进行数据验证。
- 自动处理嵌套数据模型。
- 支持 JSON 和字典序列化与反序列化。
- 支持字段级和模型级自定义验证器。
- 可以轻松定义字段的默认值和选项。

Pydantic会自动验证数据是否符合定义的类型
校验失败，抛出ValidationError


## 核心内容
```yaml
pydantic:
    class_validators: # 模型校验
        @field_validator: # 自定义模型字段校验方法
        @root_validator: # 自定义模型字段校验方法
    BaseModel: # 模型基类
        Config: # 模型配置
            anystr_strip_whitespace:
            min_anystr_length:
        dict(): # 返回字典
        json():
        parse_obj(): # 字典解析
        parse_raw(): # 字符串解析
    ValidationError:
```
