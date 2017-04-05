FROM nginx:alpine

# Install env 添加国内镜像到顶部
RUN sed -i '1i\http://mirrors.ustc.edu.cn/alpine/v3.4/main/' /etc/apk/repositories
# 添加一个无法登录的账户
#RUN  addgroup webuser && adduser  -s /sbin/nologin -D -G webuser webuser 
RUN  mkdir /data && mkdir /data/www && mkdir /data/log && mkdir /data/log/nginx
RUN  chown -R nginx:nginx /data/www /data/log

#设置时区
RUN apk update && apk add ca-certificates && \
    apk add tzdata && \
    ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    echo "Asia/Shanghai" > /etc/timezone

# config
RUN ln -sf /opt/config/nginx.conf       /etc/nginx/nginx.conf
RUN ln -sf /opt/config/fastcgi_params   /etc/nginx/fastcgi_params
RUN ln -sf /opt/config/sites-enabled    /etc/nginx/sites-enabled
RUN ln -sf /opt/config/certs            /etc/nginx/certs

EXPOSE 80
