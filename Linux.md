## Linux

- systemctl status <service>	# 查看服务运行情况
  - params: *service*
    - nginx
    - mysql

## Nginx

- /etc/nginx 配置文件夹

- nginx -s reload  # 热重载
- nginx -c nginx.conf  # 启动nginx服务

## uWSGI

- uwsgi --ini uwsgi.ini  # 启动uwsgi
- uwsgi --reload uwsgi.pid  # 重启
- uwsgi --stop uwsgi.pid  # 停止服务

## systemctl

- 服务文件夹 /etc/systemd/system/

- 注册服务 systemctl enable <file>
- 启动服务 systemctl start <service>
- 重启服务 systemctl restart <service>
- 停止服务 systemctl stop <service>
- 查看状态 systemctl status <service>

## tar

- 解压 tar -xf <file>