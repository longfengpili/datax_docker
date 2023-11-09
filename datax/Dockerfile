# 基础镜像系统
FROM ubuntu:latest

# Docker 内用户切换到 root
USER root

# 设置时区为东八区
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# 更新系统包列表并安装
RUN sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list \
    && apt-get update \
    && apt-get install -y wget python3 openjdk-8-jdk maven \
    && apt-get clean

ADD ./DataX /datax

RUN cd /datax \
    && mvn -U clean package assembly:assembly -Dmaven.test.skip=true

CMD ["tail", "-f", "/dev/null"]
