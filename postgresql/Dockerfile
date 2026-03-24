FROM swr.cn-north-4.myhuaweicloud.com/ddn-k8s/docker.io/postgres:15.6-bookworm as builder
LABEL maintainer="hq@nosugartech.com"
ARG NODE_PYTHON_PACKAGES
ENV TZ="Asia/Shanghai" \
    PATH="/opt/venv/bin:$PATH" \
    DEBIAN_FRONTEND="noninteractive"
RUN sed -i 's/deb.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list.d/debian.sources && \
    apt-get update && apt-get install -y postgresql-15-pgaudit && mkdir -p /var/lib/postgresql/conf/ && \
    wget -O /var/lib/postgresql/conf/postgresql.conf https://raw.githubusercontent.com/kinghu88/dockerfile/refs/heads/main/postgresql/postgresql.conf && \
    apt-get clean && rm -rf /var/lib/apt/lists/* && \
CMD ["postgres", "-c", "config_file=/var/lib/postgresql/conf/postgresql.conf"]