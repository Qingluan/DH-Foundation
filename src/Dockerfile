FROM qingluan/ubuntu_hadoop:latest
MAINTAINER qingluan

#install curl
RUN echo -n "start instasll curl ..."
RUN apt-get install -y curl
RUN apt-get install -y tree
RUN echo "[ok]"

#install JDK7
RUN echo "start install JDK7..."
RUN echo -n  "download JDK7 ...."
RUN cd /tmp && wget -q http://git.oschina.net/dark.H/DDataAny/raw/master/resource/jdk-8u73-linux-i586.tar -O - | tar -xvf - 
RUN echo -e " [ok]"
RUN echo -n "set JAVA's environment "
RUN mkdir -p /usr/lib/jvm 
RUN mv /tmp/jdk1.8.0_73 /usr/lib/jvm/java-8-oracle/



#set jdk
RUN update-alternatives --install /usr/bin/java java /usr/lib/jvm/java-8-oracle/bin/java 300     
RUN update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/java-8-oracle/bin/javac 300
ENV JAVA_HOME /usr/lib/jvm/java-8-oracle/
RUN echo " [ok]"



# set and install hadoop 
#

RUN echo "start  install and set hadoop "  
RUN mkdir -p /home/hadoop/opt
RUN cd /home/hadoop/opt &&  wget -q http://git.oschina.net/dark.H/DDataAny/raw/master/resource/hadoop-2.6.0.tar -O - | tar -xvf -
ENV HADOOP_HOME /home/hadoop/opt/hadoop-2.6.0
ENV PATH "$PATH:$HADOOP_HOME/bin"


#RUN apt-get install -y maven build-essential autoconf automake libtool cmake zlib1g-dev pkg-config libssl-dev libprotobuf-dev protobuf-compiler
#RUN apt-get install snappy libsnappy-dev
#RUN echo  "* Bzip2"
#RUN apt-get install bzip2 libbz2-dev
#RUN echo "* Jansson (C Library for JSON)"
#RUN apt-get install libjansson-dev
#RUN echo "* Linux FUSE"
#RUN apt-get install fuse libfuse-dev

# startup
EXPOSE 22
ENTRYPOINT /home/qingluan/en.sh


