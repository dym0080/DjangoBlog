# DjangoBlog

> 本项目用于研究 `Django` 项目，原始项目来源：https://github.com/liangliangyy/DjangoBlog

> todo: 代码基本没经过pylint检测修复。

基于 `python3.7.4` 和 `Django2.2.8` 的博客。

## 主要功能：
- 文章，页面，分类目录，标签的添加，删除，编辑等。文章及页面支持`Markdown`，支持代码高亮。
- 支持文章全文搜索。
- 完整的评论功能，包括发表回复评论，以及评论的邮件提醒，支持`Markdown`。
- 侧边栏功能，最新文章，最多阅读，标签云等。
- 支持Oauth登陆，现已有Google,GitHub,facebook,微博,QQ登录。
- 支持`Memcache`缓存，支持缓存自动刷新。
- 简单的SEO功能，新建文章等会自动通知Google和百度。
- 集成了简单的图床功能。
- 集成`django-compressor`，自动压缩`css`，`js`。
- 网站异常邮件提醒，若有未捕捉到的异常会自动发送提醒邮件。
- 集成了微信公众号功能，现在可以使用微信公众号来管理你的vps了。

## 安装

使用pip安装： `pip install -Ur requirements.txt`



### 配置
配置都是在 `setting.py` 中，部分配置迁移到了后台配置中。

很多 `setting` 配置我都是写在环境变量里面的.并没有提交到 `github` 中来.例如`SECRET_KEY`,`OAHUTH`,`mysql`以及邮件部分的配置等.你可以直接修改代码成你自己的,或者在环境变量里面加入对应的配置就可以了.

`test`目录中的文件都是为了`travis`自动化测试使用的.不用去关注.或者直接使用.这样就可以集成`travis`自动化测试了.

`bin`目录是在`linux`环境中使用`Nginx`+`Gunicorn`+`virtualenv`+`supervisor`来部署的脚本和`Nginx`配置文件.可以参考我的文章:

>[DjangoBlog部署教程](https://www.lylinux.net/article/2019/8/5/58.html)

有详细的部署介绍.


## 运行

本项目使用 `Postgres` 数据库，修改 `DjangoBlog/setting.py` 修改数据库配置，如下所示：

> 可随意选择你喜好的数据库

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'djangoblogdb',
        'USER': 'postgres',
        'PASSWORD': 'qwer1234',
        'HOST': '127.0.0.1',
        'PORT': '5432',
    }
}
```

### 创建数据库
mysql数据库中执行:
```sql
CREATE DATABASE `djangoblog` /*!40100 DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci */;
```

然后终端下执行:
```bash
py manage.py makemigrations
py manage.py migrate
```

### 创建超级用户

 终端下执行:
```bash
py manage.py createsuperuser
```

### 创建测试数据
终端下执行:
```bash
py manage.py create_testdata
```

### 收集静态文件
终端下执行:  
```bash
py manage.py collectstatic --noinput
py manage.py compress --force
```

### 开始运行：
执行： `py manage.py runserver`


浏览器打开: http://127.0.0.1:8000/  就可以看到效果了。
## 更多配置:
[更多配置介绍](/docs/config.md)


