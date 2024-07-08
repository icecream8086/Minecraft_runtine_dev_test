FROM registry.access.redhat.com/ubi9/ubi:latest
USER root
LABEL maintainer="John Doe"

# 更新镜像
RUN yum update --disablerepo=* --enablerepo=ubi-9-appstream-rpms --enablerepo=ubi-9-baseos-rpms -y && rm -rf /var/cache/yum

RUN yum update --disablerepo=* --enablerepo=ubi-9-appstream-rpms --enablerepo=ubi-9-baseos-rpms -y && \
    yum install glibc-devel zlib-devel gcc freetype-devel libstdc++-static -y && \
    rm -rf /var/cache/yum

# 下载并解压Mandrel
RUN curl -L https://github.com/graalvm/mandrel/releases/download/mandrel-23.0.4.1-Final/mandrel-java17-linux-amd64-23.0.4.1-Final.tar.gz | tar -xz -C /opt/

# 设置环境变量
ENV JAVA_HOME=/opt/mandrel-java17-23.0.4.1-Final
ENV GRAALVM_HOME=${JAVA_HOME}
ENV PATH=${JAVA_HOME}/bin:${PATH}

WORKDIR /root
# 暴露必要的端口
EXPOSE 25565

CMD ["/root/run.sh"]