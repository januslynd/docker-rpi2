FROM com.github.januslynd/rpi2-java:8

ENV EL_VERSION 2.2.0

# Installing wget in order to download elasticsearch from elastic.co
RUN pacman --noconfirm -S wget

USER elasticsearch
RUN cd /usr/share && \
    wget https://download.elasticsearch.org/elasticsearch/release/org/elasticsearch/distribution/tar/elasticsearch/$EL_VERSION/elasticsearch-$EL_VERSION.tar.gz && \
    tar -xvzf elasticsearch-$EL_VERSION.tar.gz && \
    rm elasticsearch-$EL_VERSION.tar.gz && \
    ln -s elasticsearch-$EL_VERSION logstash

# Making elasticsearch available
ENV PATH /usr/share/elasticsearch-$EL_VERSION/bin:$PATH

WORKDIR /usr/share/elasticsearch-$EL_VERSION

COPY config ./config
VOLUME ./data
EXPOSE 9200 9300
