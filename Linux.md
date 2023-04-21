## Linux

- systemctl status <service>	# 查看服务运行情况
  - params: *service*
    - nginx
    - mysql

## Nginx

- /ect/nginx 配置文件夹

- nginx -s reload  # 热重载
- nginx -c nginx.conf  # 启动nginx服务

## uWSGI

- uwsgi --ini uwsgi.ini  # 启动uwsgi
- uwsgi --reload uwsgi.pid  # 重启
- uwsgi --stop uwsgi.pid  # 停止服务