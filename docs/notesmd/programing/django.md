# django 的使用

## django web开发非常敏捷
1. python3有非常多很好的库，比如biopython, beautiful soap, pandas, numpy, matplotlib

2. python3本身的函数用起来很方便，语言优美

3. python3有很好的ide，比如anocanda中集成的spyder

## django url

## view 中获取参数的方法

## form

## view中使用自己定义的类和函数

## django导入数据
```
# managy.py 所在的目录
django_path = "F:\\django\\try-django-19-master\\src"

os.chdir(django_path) # 切换目录

os.getcwd() # 获取当前目录

# run manage.py
# 这句话还不懂啊
os.environ.setdefault("DJANGO_SETTINGS_MODULE", "trydjango19.settings")

from django.core.management import execute_from_command_line

execute_from_command_line(sys.argv)

from posts.models import Post

```

# Django shell

这个教程还不错[ziqiangxuetang](http://code.ziqiangxuetang.com/django/django-schema-migration.html)
打开你本地的终端(不是在Python解析器里面) 然后输入这个命令:
`python manage.py shell`

数据库迁移和更新遇到的问题
1. 清除数据库中所有的信息, 只保留表的结构, `python manage.py flush`
2. 添加超级用户: `python manage.py createsuperuser`
3. 如果数据库中有表且有数据的话, 修改model之后再查询数据会出错, 可以回到第一步先删除数据
4. 更新model的方法：`python manage.py makemigrations`然后`python manage.py migrate`

## uwsgi
uwsgi --ini /etc/uwsgi9090.ini
uwsgi --stop /etc/uwsgi9090.ini

## 缓存
vi trydjango19/settings.py