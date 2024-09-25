# Django

>
>``
>


## 基础介绍


MVT模式

### 项目结构
```yaml
django项目:
    /app:
        /migrations:
            __init__.py:
        __init__.py:
        admin.py:
        apps.py:
        models.py:
        tests.py:
        urls:
        views.py:
    /project:
        __init__.py:
        asgi.py:
        settings.py:
        urls.py:
        wsgi.py:
    /templates:
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

#### urls.py
```yaml
urls.py:
    urlpatterns: # 定义url视图路径映射
```



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
```


## 核心内容
```yaml
django:
    contrib:
        admin:
    db:
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
            ForeignKey:
                to:
                to_field:
            ImageField:
            IntegerField:
            Model:
                objects: # 模型操作类
                    all():
                    create():
                    delete():
                    filter():
                    first():
                    get():
                    update():
                delete():
                save():
            SmallIntegerField:
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
                method:
                POST:
        response:
            JsonResponse:
    shortcuts:
        redirect():
        render(): # 视图渲染
    urls:
        include:
        path:
    VERSION: # 版本
    get_version():

rest_framework:
    routers:
        DefaultRouter:
    serializers:
        Serializer:
```


### 模板引擎