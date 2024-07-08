FROM registry.access.redhat.com/ubi9/ubi
USER root
LABEL maintainer="John Doe"
# Update image
RUN yum update --disablerepo=* --enablerepo=ubi-9-appstream-rpms --enablerepo=ubi-9-baseos-rpms -y && rm -rf /var/cache/yum
RUN yum install --disablerepo=* --enablerepo=ubi-9-appstream-rpms --enablerepo=ubi-9-baseos-rpms httpd wget -y && rm -rf /var/cache/yum
RUN yum install vim java-17-openjdk -y && rm -rf /var/cache/yum
# Expose the necessary port
EXPOSE 25565