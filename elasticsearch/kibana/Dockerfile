FROM kibana:6.4.2
MAINTAINER chentf "tfchen5211@foxmail.com"

#ENV TZ=Asia/Shanghai
#RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN mkdir -p /usr/share/kibana/customer/config/
RUN mv /usr/share/kibana/config/kibana.yml /usr/share/kibana/customer/config/kibana.yml
RUN ln -s /usr/share/kibana/customer/config/kibana.yml /usr/share/kibana/config/kibana.yml