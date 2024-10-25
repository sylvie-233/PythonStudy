# Django

>
>`知了传课Django5教程：P24`
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
    app_name: # 路由命名空间
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
    startapp:
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
        auth:
        contenttypes:
        messages:
        sessions:
        staticfiles:
    db:
        backends:
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
            ForeignKey:
                to:
                to_field:
            ImageField:
            IntegerField:
            Model: # 模型基类
                objects: # 模型操作类
                    all(): # 所有数据
                    create():
                    delete():
                    filter(): # 条件过滤
                    first():
                    get():
                    order_by():
                    update():
                delete():
                save(): # 添加数据
            SmallIntegerField:
        connection:
            cursor():
                close():
                execute():
                fetchall():
                rowcount():
    forms: # 表单模型
        CharField:
        ChoiceField:
            choices:
            validators:
        Form:
        ModelChoiceField:
            queryset:
        ModelForm:
            Meta:
                error_messages:
                exclude:
                fields:
                model: # 指定模型类
                widgets:
    http:
        request:
            Request: # 请求对象
                GET: # 字典
                POST:
                method:
        response:
            JsonResponse:
        HttpResponse:
    shortcuts:
        HttpResponse: # 基础响应对象
        redirect():
        render(): # 视图渲染
            context:
    template:
        loader:
            render_to_string():
    urls:
        include():
        path(): # 定义路径 视图函数映射
            name: # 路由命名
        reverse(): # 路由反转
            kwargs:
    VERSION: # 版本
    get_version():

rest_framework:
    routers:
        DefaultRouter:
    serializers:
        Serializer:
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



### 中间件




### 异常处理



### ORM


#### 一对一



#### 一对多





#### 多对多




### 模板引擎


#### DTL

```yaml
Django Template Language:
    {{ var }}:
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
        load static:
        static:
        url:
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



### 页面组件



### 权限校验



### Contrib





