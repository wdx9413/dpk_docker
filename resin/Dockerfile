FROM centos:7
MAINTAINER weidx "weidongxuan@kaoshixing.com"
RUN mkdir -p /home/work/bin/
RUN mkdir -p /home/work/software/
RUN mkdir -p /home/work/log/
WORKDIR /home/work/

# jdk7
ADD https://ksxing-deploy.oss-cn-beijing.aliyuncs.com/new_software/jdk-7u79-linux-x64.tar.gz /home/work/software/
RUN tar xvfz /home/work/software/jdk-7u79-linux-x64.tar.gz -C /home/work/software/
ENV JAVA_HOME /home/work/software/jdk1.7.0_79
ENV JRE_HOME ${JAVA_HOME}/jre
ENV JAVA_BIN ${JAVA_HOME}/bin
ENV PATH ${JAVA_HOME}/bin:$PATH
ENV CLASSPATH .:${JAVA_HOME}/lib/dt.jar:${JAVA_HOME}/lib/tools.jar
# RUN ln -s /home/work/software/jdk1.7.0_79/bin/java /usr/bin/java
# resin
ADD https://ksxing-deploy.oss-cn-beijing.aliyuncs.com/new_software/resin-pro-4.0.43-1.x86_64.rpm /home/work/software/
RUN yum -y install unzip zip openssl-devel glibc-devel
RUN rpm -ivh /home/work/software/resin-pro-4.0.43-1.x86_64.rpm
COPY config/* /etc/resin/
RUN mkdir -p /home/work/bin/ksxing-web-{login,index,baseinfo,setting,examadmin,analysis,course,process,exam,data}/{tmp,backup}
RUN mkdir -p /home/work/store/{oss,certificate,error_book,exam,exam_analysis,exam_result}
RUN chown -R resin:resin /home/work/store /home/work/bin
# 微软字体
RUN yum -y install fontconfig
RUN mkdir /usr/share/fonts/zh_CN
ADD https://ksxing-deploy.oss-cn-beijing.aliyuncs.com/new_software/msyh.ttf /usr/share/fonts/zh_CN
RUN fc-cache -fv
# wkhtmltopdf
ADD https://ksxing-deploy.oss-cn-beijing.aliyuncs.com/new_software/wkhtmltox-0.12.5-1.centos7.x86_64.rpm /home/work/software
RUN yum -y install libX11 libXext libXrender libjpeg openssl xorg-x11-fonts-75dpi xorg-x11-fonts-Type1
RUN rpm -ivh /home/work/software/wkhtmltox-0.12.5-1.centos7.x86_64.rpm
VOLUME ["/home/work/bin/"]
EXPOSE 9045 
EXPOSE 9046 
EXPOSE 9047
EXPOSE 9048
EXPOSE 0949
EXPOSE 9050
EXPOSE 9051
EXPOSE 9052
EXPOSE 9053
EXPOSE 9054
RUN echo success-over
CMD resinctl start-all && /bin/bash
#CMD ["/bin/bash"]

