FROM centos
MAINTAINER chesley1979 "80363639@qq.com"

RUN set -ex; \
	rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
RUN set -ex; \
	yum install -y zlib zlib-devel openssl openssl-devel net-tools
RUN set -ex; \
	yum install -y gcc* make 

COPY sysctl.conf /etc/
COPY limits.conf /etc/security/
COPY 20-nproc.conf /etc/security/limits.d/
COPY config /etc/selinux/


