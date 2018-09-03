FROM mycentos:r2

COPY redis-4.0.9.tar.gz /usr/local/src/
RUN set -ex; \
	cd /usr/local/src; \
	tar -zxvf redis-4.0.9.tar.gz; \
	cd redis-4.0.9; \
	make -j4 && make install; \
	\cp src/redis-trib.rb /usr/local/bin/; \
	cd .. && rm -rf redis-4.0.9*
RUN set -ex; \
	yum -y history undo `yum history list gcc* |awk -F\| '{print $1}' |sed -n '4p'`	
VOLUME /data
WORKDIR /data

COPY sysctl.conf /etc/
COPY limits.conf /etc/security/
COPY 20-nproc.conf /etc/security/limits.d/
COPY config /etc/selinux/
COPY redis.conf /data
ENTRYPOINT ["redis-server"]

EXPOSE 6380
EXPOSE 16380
CMD ["redis.conf"]
