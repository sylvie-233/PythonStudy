# Django

>
>`知了传课Django5教程：P57`
>


## 基础介绍

project -> app

每一个app包含一个子路由的所有东西

MVT模式

### 项目结构
```yaml
django项目:
    /app: # 应用目录
        /migrations:
            __init__.py:
        /templates:
        __init__.py:
        admin.py:
        apps.py:
        forms.py:
        models.py:
        tests.py:
        urls:
        views.py:
    /project: # 项目目录
        __init__.py:
        asgi.py:
        settings.py:
        urls.py:
        wsgi.py:
    /static:
    /templates: # 页面模板
    db.sqlite3:
    manage.py:
```

#### settings.py
```yaml
settings.py:
    ALLOWED_HOSTS:
    DATABASES:
        default:
            ENGINE:
            HOST:
            NAME:
            PORT:
            USER:
    DEBUG:
    INSTALLED_APPS:
    STATIC_URL: # 静态资源url
    STATICFILES_DIRS: # 静态资源目录
    TEMPLATES: # 模板配置
        BACKEND:
        DIRS:
        APP_DIRS:
        OPTIONS:
```

项目配置文件


#### urls.py
```yaml
urls.py:
    app_name: # 路由命名空间(数据库迁移时带上app_name前缀)
    urlpatterns: # 定义url视图路径映射
```

定义url与app视图函数映射



### django-admin
```yaml
django-admin:
    startapp: # 创建应用
    startproject: # 创建项目
```

### manage.py
```yaml
manage.py:
    makemigrations: # 数据库迁移
    migrate: # 生成数据库迁移文件
    runserver: # 开发服务器运行
    startapp: # 生成项目app
```


## 核心内容
```yaml
django:
    conf:
        settings:
        urls:
            static:
                static():
    contrib:
        admin:
        auth: # django内置登录校验
            context_processors:
                auth:
            decorators:
                @login_required:
                    login_url:
            models:
                User:
                    objects:
                        create_user():
                    check_password():
                    get_username():
                    is_authenticated():
            get_user_model():
            login():
            logout():
        contenttypes:
        messages:
            context_processors:
                messages:
        sessions:
        staticfiles:
    core:
        mail:
            backends:
                smtp:
                    EmailBackend:
            send_mail(): # 发送邮件
        serializers:
            serialize():
        validators: # 表单校验器
            RegexValidator:
    db:
        backends:
            mysql:
            sqlite3:
        migrations:
            Migration:
                dependencies:
                initial:
                operations:
            CreateModel(): # 迁移模型
                name:
                fields:
        models:
            BigAutoField:
            CharField:
                max_length:
            DateTimeField:
                auto_now_add:
            ForeignKey: # 模型外键
                on_delete:
                    CASCADE:
                related_name: # 反向引用字段名(默认xxx_set)
                to: # 关联的模型
                to_field:
            ImageField:
            IntegerField:
            ManyToManyField: # 多对多关联字段
                to:
                related_name: # 反向引用字段名
            Model: # 模型基类
                Meta: # 模型元信息
                    db_table: # 模型表名
                    ordering:
                objects: # 模型操作类 Queryset
                    aggregate(): # 聚合查询
                    all(): # 所有数据
                    annotate(): # 查询结果添加字段（常用于聚合查询）
                    create():
                    delete():
                    exists():
                    filter(): # 条件过滤
                        query: # SQL查询语句
                        __contains: ## like %% 模糊查询
                        __date: # 日期
                        __endwith:
                        __exact: # 精确查询
                        __gt: # >
                        __iexact: # like模糊查询
                        __in:
                        __range:
                        __regex:
                        __startwith:
                    first():
                    get():
                    order_by():
                    update():
                    update_or_create():
                delete():
                save(): # 添加数据
            OneToOneField: # 一对一关联字段
                on_delete:
                to:
            SmallIntegerField:
            Avg(): # 平均数
            Count(): # 个数
            F(): # 字段计算
            Max(): # 最大值
            Min(): # 最小值
            Q(): # 查询语句（规范查询嵌套）
            Sum(): # 求和
        connection:
            cursor():
                close():
                execute():
                fetchall():
                rowcount():
    forms: # 表单模型
        BooleanField:
        CharField:
            error_messages:
            label:
            max_length:
            min_length:
            validators: # 字段校验器
            widget: # 页面展示所用组件（默认输入框input）
        ChoiceField:
            choices:
            require:
            validators:
        EmailField:
        Form: # 表单基类
            cleaned_data: # 表单数据（字典）
            errors: # 表单校验错误信息
                as_json():
                get_json_data():
            add_error():
            clean_[field](): # 自定义表单字段校验
            is_valid(): # 表单数据校验
        ModelChoiceField:
            queryset:
        ModelForm: # 模型+表单（避免Model和Form中字段的重复编写）
            Meta: # 元信息
                error_messages: # 字段校验错误信息
                exclude:
                fields: # 指定模型中的字段
                model: # 指定模型类
                widgets:
            errors:
            is_valid():
            save(): # 保存到数据库
        Textarea: # 文本域组件
        ValidationError:
    http:
        request:
            Request: # 请求对象
                COOKIES:
                GET: # 字典
                POST:
                method: # 请求方法
                session:
                    get():
                    set_expiry():
        response:
            JsonResponse:
        HttpResponse:
            delete_cookie():
            set_cookie():
                key:
                value:
                max_age:
                expires:
                path:
                domain:
    shortcuts:
        HttpResponse: # 基础响应对象
        redirect():
        render(): # 视图渲染
            context: # 上下文变量
        reverse(): # 反向引用
        reverse_lazy(): # 反向引用
    template:
        context_processors:
            debug:
            request:
        loader:
            render_to_string():
    urls:
        include():
        path(): # 定义路径 视图函数映射
            name: # 路由命名
        re_path():
        reverse(): # 路由反转
            kwargs:
    views:
        decorators:
            http:
                @require_http_methods():
    VERSION: # 版本
    get_version():

rest_framework:
    response:
        Response:
    routers:
        DefaultRouter:
    serializers:
        CharField:
            error_messages:
            max_length:
        IntegerField:
        Serializer: # 序列化器（模型）,
            data:
            many:
            validate():
            validate_field():
        ValidationError:
    views:
        APIView: # API控制器类
            as_view(): # 转换为视图函数
            get():
```

<br />
<br />

### 视图函数

views控制器

```python
def funcName(request):
    return HttpResponse("响应内容")
```

path param -> query string -> post form

path param类型指定
- int
- str
- uuid
- slug
- path



project urls -> app urls

urls嵌套 -> include()引入 （实现路由嵌套）



<br />
<br />


### 参数校验

Form可实现表单参数校验、ModelForm自定义表单字典校验：`Form.clean_[field]()`

DRF的序列化器可实现参数校验

<br />
<br />

### 中间件

#### CSRF

```html
<input type="hidden" name="csrfmiddlewaretoken" value="{{ csrf_token }}">

{% csrf_token %}
```

<br />
<br />


### 异常处理



### ORM


#### QuerySet

`filter()`、`exclude()`、`get()`

`字段名__condition`条件查询




#### 一对一
```python
class User(models.Model):
    name = models.CharField()

class Article(models.Model):
    content = models.TextField()
    author = models.ForeignKey("User")

article = Article(content="内容")
article.author = User(name="名称")
article.save()
```

`OneToOneField`

外键关联自动生成`author_id`外键字段



<br />
<br />


#### 一对多

```python
articles = user.article_set.all()
```


一对多使用对应外键字段：`xxx_set`


<br />
<br />




#### 多对多

`ManyToManyField`

自动生成中间表：`table1_table2`



<br />
<br />

### 模板引擎


#### DTL

```yaml
Django Template Language:
    {{ variable }}:
        user:
    {% %}:
        extends block endblock:
        for in empty endfor:
            forloop:
                counter:
                counter0:
                first:
                last:
        if elif else endif:
        include:
        with endwith:
    func: # 常用函数
        load static: # 加载静态文件
        static:
        url: # 反向引用视图函数
    filter: # 常用过滤器
        add:
        cut:
        date:
        default:
        default_if_none:
        join:
        length:
        lower:
        safe:
        slice:
        truncatechars:
        upper:
```

Django内置模板引擎


### 页面组件

ModelForm：将Form和Model结合起来的模型


### 权限校验


contrib.auth



### Contrib





