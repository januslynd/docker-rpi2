FROM com.github.januslynd/rpi2-java:8

ENV EL_VERSION 2.2.0

# Adding elasticsearch user
RUN useradd -ms /bin/bash elasticsearch

# Installing wget in order to download elasticsearch from elastic.co
RUN pacman --noconfirm -S wget

RUN cd /usr/share && \
    wget https://download.elasticsearch.org/elasticsearch/release/org/elasticsearch/distribution/tar/elasticsearch/$EL_VERSION/elasticsearch-$EL_VERSION.tar.gz && \
    tar -xvzf elasticsearch-$EL_VERSION.tar.gz && \
    rm elasticsearch-$EL_VERSION.tar.gz && \
    ln -s elasticsearch-$EL_VERSION logstash

# Making elasticsearch available
ENV PATH /usr/share/elasticsearch-$EL_VERSION/bin:$PATH

# Set the working dir
WORKDIR /usr/share/elasticsearch-$EL_VERSION

# Setting ownership
RUN set -ex \
	&& for path in \
		./data \
		./logs \
		./config \
		./config/scripts \
	; do \
		mkdir -p "$path"; \
		chown -R elasticsearch:elasticsearch "$path"; \
	done

# Copying configuration files
COPY config ./config
VOLUME ./data

# Exposing elastic search default ports
EXPOSE 9200 9300

# Execution now on as elasticsearch user
USER elasticsearch
