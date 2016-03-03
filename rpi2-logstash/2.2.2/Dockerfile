FROM com.github.januslynd/rpi2-java:8

ENV LS_VERSION 2.2.2

# Installing wget in order to download logstash from elastic.co
RUN pacman --noconfirm -S wget

RUN cd /opt && \
    wget https://download.elastic.co/logstash/logstash/logstash-$LS_VERSION.tar.gz && \
    tar -xvzf logstash-$LS_VERSION.tar.gz && \
    rm logstash-$LS_VERSION.tar.gz && \
    ln -s logstash-$LS_VERSION logstash

# Making available logstash
ENV PATH /opt/logstash/bin:$PATH
ENV LS_HEAP_SIZE 64m

# Ommiting previous JAVA_OPTS. JRuby may need special syntax.
ENV JAVA_OPTS=
