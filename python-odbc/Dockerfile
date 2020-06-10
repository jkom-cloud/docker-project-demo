FROM ubuntu:18.04
EXPOSE 5000
WORKDIR /app
RUN sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list \
    && apt-get update && apt update -y \
    && apt install -y curl python3.7 python3-pip unixodbc-dev \
    && apt install -y git \
    && ln -s /usr/bin/python3 /usr/bin/python \
    && ACCEPT_EULA=Y apt-get install -y default-libmysqlclient-dev build-essential \
    && curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add - \
    && curl https://packages.microsoft.com/config/ubuntu/18.04/prod.list > /etc/apt/sources.list.d/mssql-release.list \
    && apt-get update \
    && ACCEPT_EULA=Y apt-get install -y --allow-unauthenticated msodbcsql17 \
    && ACCEPT_EULA=Y apt-get install -y --allow-unauthenticated --assume-yes mssql-tools \
    && apt install -y libgssapi-krb5-2 \
    && echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile \
    && echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc \
    && apt purge --auto-remove -y curl \
    && apt clean