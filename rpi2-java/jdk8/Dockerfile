FROM com.github.januslynd/rpi2-arch

RUN mkdir /java
COPY jdk-8u73-linux-arm32-vfp-hflt.tar.gz /java
RUN cd /java/ && \
    tar xf jdk-8u73-linux-arm32-vfp-hflt.tar.gz

ENV JAVA_HOME=/java/jdk1.8.0_73
ENV PATH=$JAVA_HOME/bin:$PATH
ENV JAVA_OPTS="-Djava.security.egd=file:/dev/./urandom -Djava.awt.headless=true -Xmx512m -XX:+UseConcMarkSweepGC"
