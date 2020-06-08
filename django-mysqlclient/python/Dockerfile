FROM python:3.7-alpine
LABEL maintainer="chi.liu@jiukangyun.com"

EXPOSE 8001
ENV PYTHONUNBUFFERED=1

WORKDIR /app
COPY . /app

RUN sed -i 's/dl-cdn.alpinelinux.org/mirror.tuna.tsinghua.edu.cn/g' /etc/apk/repositories \
    && apk add --no-cache mariadb-connector-c \
    && apk add --no-cache --virtual=build-deps mariadb-connector-c-dev build-base linux-headers \
    && pip install --no-cache-dir -i https://mirrors.aliyun.com/pypi/simple -r requirements.txt \
    && apk del build-deps \
    && rm -rf /root/.cache /tmp/*
