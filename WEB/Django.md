# Django

`Django REST Framework series: P3`

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
        permissioins.py:
        serializers.py:
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
    AUTH_USER_MODEL:
    AUTHENTICATION_BACKENDS: # 认证后端
        django.contrib.auth.backends.ModelBackend:
    DATABASE_ROUTERS: # 数据库路由器（基于规则切换数据源）
    DATABASES: # 数据库配置（可动态切换）
        default: # 默认数据库
            ENGINE:
            HOST:
            NAME:
            PORT:
            USER:
    DEBUG:
    INSTALLED_APPS: # 安装的APP应用(6个默认安装)
        django.contrib.admin:
        django.contrib.auth:
        django.contrib.contenttypes:
        django.contrib.sessions:
        django.contrib.messages:
        django.contrib.staticfiles:
    LANGUAGE_CODE: # 语言
    STATIC_URL: # 静态资源url
    STATICFILES_DIRS: # 静态资源目录
    TEMPLATES: # 模板配置
        BACKEND:
        DIRS:
        APP_DIRS:
        OPTIONS:
    TIME_ZONE: # 时区
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
    help:
    runserver:
        --settings:
    startapp: # 创建应用
    startproject: # 创建项目
```


django脚手架命令




### manage.py
```yaml
manage.py:
    createsuperuser: # 创建admin超级管理员
    drf_create_token:
    graph_models:
    makemigrations: # 生成数据库迁移文件
    migrate: # 数据库迁移
    runserver: # 开发服务器运行
    startapp: # 生成项目app
```


django项目脚本命令
会自动把项目路径和 settings.py 加载到 PYTHONPATH，这样命令就可以访问项目的配置和环境（而django-admin则没有）
- 内部调用了 django-admin 的功能
- 添加项目路径到 sys.path
- 设置环境变量 DJANGO_SETTINGS_MODULE 为项目的 settings.py
- 调用 django.core.management 模块执行命令




## 核心内容
```yaml
django:
    apps: # 应用
        AppConfig:
            name:
            verbose_name:
    conf: # 配置
        settings: # 项目配置项引用
        urls:
            static:
                static():
    contrib: # 第三方
        admin:
            site:
                url:
                register(): # 后台注册模型
            ModelAdmin: # Admin管理模型（与Model绑定）
                Meta:
                    verbose_name: # 显示名称
                list_display: # 展示字段（Model模型）
                list_filter:
                search_fields:
            @register():
        auth: # django内置登录校验
            backends:
                BaseBackend:
            context_processors:
                auth:
            decorators: # 装饰器
                @login_required: # 登录校验
                    login_url:
                @permission_required: # 权限校验 
            models:
                AbstractBaseUser:
                AbstractUser: #     
                AnonymousUser:
                UserManager:
                Group: # 组（用户分组）
                    permissions: # 组权限     
                Permission: # 权限
                    codename:
                    content_type:
                    name:
                User: # 用户模型
                    date_joined: # 注册时间
                    email:
                    is_active: # 是否有效
                    is_staff: # 是否可登录 admin 后台
                    is_superuser: # 是否是超级用户
                    last_login: # 最后登录时间
                    password:
                    username:
                    ---
                    groups: # 用户所属组
                    objects:
                        create_user():
                    user_permissions: # 用户权限
                    check_password():
                    get_username():
                    has_perm(): # 权限校验
                    is_authenticated():
            authenticate(): # user用户认证
            get_user_model():
            login(): # 登入
            logout(): # 登出
        contenttypes:
        messages:
            context_processors:
                messages:
        sessions:
        staticfiles:
    core: # 核心
        mail:
            backends:
                smtp:
                    EmailBackend:
            send_mail(): # 发送邮件
        management:
            base:
                BaseCommand: # 命令基类
                    handle():
        serializers: # 序列化
            serialize():
        signals: # 信号
            got_request_exception:
            request_finished:
            request_started:
        validators: # 表单校验器
            RegexValidator:
    db: # 数据库
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
        models: # 模型
            signals: # orm信号
                pre_delete:
                pre_save:
                post_delete:
                post_save:
            BigAutoField:
            CharField: # 字符串字段
                max_length:
            DateTimeField: # 日期时间字段
                auto_now_add:
            DecimalField: # 浮点数字段
            ForeignKey: # 模型外键
                on_delete: # 关联删除
                    CASCADE:
                related_name: # 反向引用字段名(默认xxx_set)
                to: # 关联的模型
                to_field:
            ImageField:
            IntegerField:
            Manager: # 全局拦截器
                create():
            ManyToManyField: # 多对多关联字段
                through: # 中间表（类）
                to:
                related_name: # 反向引用字段名
            Model: # 模型基类
                Meta: # 模型元信息
                    db_table: # 模型表名
                    ordering:
                    permissions: # 权限
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
                    using(): # 切换数据源
                clean(): # 数据提交校验钩子
                delete(): # 删除数据钩子
                save(): # 添加数据钩子
            OneToOneField: # 一对一关联字段
                on_delete:
                to:
            SmallIntegerField:
            TextChoices:
            TextField: # 文本字段
            UUIDField:
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
    dispatch: # 信号机制
        Signal: # 信号
            send(): # 发送信号
        @receiver(): # 信号接收
            sender: # 指定发送者
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
    http: # HTTP
        request:
            Request: # 请求对象
                COOKIES:
                GET: # 字典
                POST:
                auth:
                method: # 请求方法
                session:
                    get():
                    set_expiry():
                user:
        response:
            JsonResponse:
        HttpResponse: # HTTP响应
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
        get_object_or_404():
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
    utils:
        lorem_ipsum:
    views: # 视图函数
        decorators:
            csrf:
                @csrf_exempt():
                @csrf_protect():
            http:
                @require_http_methods():
        View:
    VERSION: # 版本
    get_version():

rest_framework:
    authentication:
        BasicAuthentication:
    authtoken: # token存储在数据库中
        models:
            Token:
        views:
            obtain_auth_token:
    decorators:
        @api_view(): # 视图函数
        @authentication_classes():
        @permission_classes():
    generics:
        ListAPIView:
        ListCreateAPIView:
            queryset:
            serializer_class:
            perform_create():
    mixins:
        DestroyModelMixin:
        UpdateModelMixin:
    pagination:
    parsers:
        FormParser:
        JSONParser:
        MultiPartParser:
    permissions:
        BasePermission: # 权限基类
            has_object_permission():
                request:
                view:
                obj:
        IsAdminUser:
        IsAuthenticated:
        IsAuthenticatedOrReadOnly:
    renders:
        BrowsableAPIRenderer:
        JSONRenderer:
    response:
        Response: # 响应对象
    routers:
        DefaultRouter:
    schemas:
        AutoSchema:
        get_schema_view():
    serializers: # 序列化模型
        CharField:
            error_messages:
            max_length:
        HyperlinkedModelSerializer:
        IntegerField:
        ModelSerializer: # 序列化模型基类
            Meta:
                fields:
                model: # 关联的模型Model
            data: # 数据
            errors:
            instance: # 模型实例
            many:
            is_valid(): # 字段校验
            save():
            validate_xxx(): # 字段校验
        ReadOnlyField:
            source:
        Serializer: # 序列化器（模型基类）,
            data:
            many:
            validate():
            validate_field():
        ValidationError: # 字段校验异常
    status:
    urls:
    views:
        APIView: # API控制器类
            authentication_classes: # 认证校验器
            permission_classes:
            as_view(): # 转换为视图函数
            delete():
            get():
            post():
    viewsets:
        ModelViewSet: # 视图集基类
            queryset:
            serializer_class:
            as_view():
                get:
                post:
            perform_create():
                serializer:
```


### 视图函数



#### View

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


#### Form

原始表单模型，用于表单校验


#### ModelForm


ModelForm: 根据模型（Model）自动生成表单字段，并支持直接保存到数据库。
- 把 Form 表单系统 和 ORM 模型 自动结合起来，帮你省去手动定义表单字段、手动验证和手动保存的步骤


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


django自带ORM框架



#### QuerySet

`filter()`、`exclude()`、`get()`

`字段名__condition`条件查询



#### Manage

全局拦截器




#### OneToOneField
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


#### OneToMany

```python
articles = user.article_set.all()
```


一对多使用对应外键字段：`xxx_set`





#### ManyToManyField

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


#### ModelForm

ModelForm：将Form和Model结合起来的模型


### 认证/权限


`django.contrib.auth`


#### User



### 信号

`django.dispatch.Signal`
- orm信号
- http信号


信号机制：
- Signal：事件的定义，例如 pre_save、post_save
- Sender：谁发的信号（通常是模型类）
- Receiver：信号的接收者（回调函数）
- send：主动触发信号
- connect：注册接收函数到信号



#### Signal



### 命令


#### Command




### Contrib

#### Django-Admin

`/admin`：访问admin管理后台



## DRF

Django Rest API

- 序列化
- 视图
- 路由
- 配置
- 认证
- 权限
- 解析器
- 验证
- 分页
- 异常处理
- 缓存
- 测试


### 项目配置

#### settings.py
```yaml
REST_FRAMEWORK:
    DEFAULT_AUTHENTICATION_CLASSES:
    DEFAULT_PAGINATION_CLASS:
    DEFAULT_PERMISSION_CLASS:
    DEFAULT_RENDER_CLASSES:
```


DRF项目配置


#### urls.py
```python
router = DefaultRouter()
router.register(prefix, viewset)

urlpatterns = [
    path("/", include("rest_framework.urls"))
    path("/", router.urls)
]
```

可使用Router注册路由



### Serializer

可实现字段校验

ModelSerializer


### 视图函数

原生视图函数
- 函数视图 `func(request)`
- 类视图 `View::get(request)`

DRF视图函数
```python
@api_view(["GET"])
def course_list(request):
    return Response(data, status)

class MyApi(APIView):
    def get(self, request):
        return Response(data, status)
```

函数视图、类视图、通用视图、视图集

### 认证/权限

authtoken、中间件

`permissions.BasePermission::has_object_permission()`



### API文档