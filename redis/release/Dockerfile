FROM centos


RUN set -ex; \
	yum install -y zlib zlib-devel openssl openssl-devel net-tools
RUN set -ex; \
	yum install -y gcc* make 
COPY ruby-2.5.1.tar.gz /usr/local/src/
RUN set -ex; \
	cd /usr/local/src; \
	tar -zxvf ruby-2.5.1.tar.gz; \
	cd ruby-2.5.1; \
	./configure && make -j4 && make install; \
	gem install redis; \
	cd .. && rm -rf ruby-2.5.1*
	
