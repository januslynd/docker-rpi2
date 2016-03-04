FROM com.github.januslynd/rpi2-arch

# add our user and group first to make sure their IDs get assigned consistently
RUN groupadd -r kibana && useradd -r -m -g kibana kibana

ENV KIBANA_VERSION 4.4.1

RUN cd /opt/kibana && \
    wget https://download.elastic.co/kibana/kibana/kibana-$KIBABA_VERSION-linux-x86.tar.gz && \
    tar -xvzf kibana-$KIBANA_VERSION.tar.gz && \
    rm kibana-$KIBANA_VERSION.tar.gz && \
    ln -s kibana-$KIBANA_VERSION logstash && \
    chown -R kibana:kibana /opt/kibana \

ENV PATH /opt/kibana/bin:$PATH

COPY docker-entrypoint.sh /

EXPOSE 5601

USER kibana