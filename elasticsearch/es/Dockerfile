FROM elasticsearch:6.4.2
MAINTAINER chentf "tfchen5211@foxmail.com"

ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN mkdir -p /usr/share/elasticsearch/customer/config
RUN mv /usr/share/elasticsearch/config/elasticsearch.yml /usr/share/elasticsearch/customer/config/elasticsearch.yml
RUN mv /usr/share/elasticsearch/config/jvm.options /usr/share/elasticsearch/customer/config/jvm.options
RUN mv /usr/share/elasticsearch/config/log4j2.properties /usr/share/elasticsearch/customer/config/log4j2.properties
RUN ln -s /usr/share/elasticsearch/customer/config/elasticsearch.yml /usr/share/elasticsearch/config/elasticsearch.yml
RUN ln -s /usr/share/elasticsearch/customer/config/jvm.options /usr/share/elasticsearch/config/jvm.options
RUN ln -s /usr/share/elasticsearch/customer/config/log4j2.properties /usr/share/elasticsearch/config/log4j2.properties