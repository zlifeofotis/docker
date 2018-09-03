FROM mycentos:r10
MAINTAINER chesley1979 "80363639@qq.com"

RUN mkdir /app
COPY jdk-8u171-linux-x64.rpm /usr/local/src/
COPY resin-4.0.56.tar.gz /usr/local/src/
RUN set -ex; \
	cd /usr/local/src; \
	rpm -ivh jdk-8u171-linux-x64.rpm; \
	export JAVA_HOME=/usr/java/default; \
	export PATH=$PATH:/usr/java/default/bin; \
	tar -zxvf resin-4.0.56.tar.gz; \
	cd resin-4.0.56; \
	./configure --prefix=/app/resin --enable-64bit; \
	make -j4 && make install; \
	cd .. && rm -rf *
RUN set -ex; \
	yum -y history undo `yum history list gcc* |awk -F\| '{print $1}' |sed -n '4p'`	

COPY *.xml /app/resin/conf/
COPY resin.properties /app/resin/conf

WORKDIR /app

ENTRYPOINT ["resin/bin/resin.sh"]

EXPOSE 8080
CMD ["console"]
