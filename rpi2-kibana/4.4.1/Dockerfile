FROM com.github.januslynd/rpi2-arch

# add our user and group first to make sure their IDs get assigned consistently
RUN groupadd -r kibana && useradd -r -m -g kibana kibana

ENV KIBANA_VERSION 4.4.1

RUN cd /opt && \
    curl -O https://download.elastic.co/kibana/kibana/kibana-$KIBANA_VERSION-linux-x86.tar.gz && \
    tar -xvzf kibana-$KIBANA_VERSION.tar.gz && \
    rm kibana-$KIBANA_VERSION.tar.gz && \
    ln -s kibana-$KIBANA_VERSION kibana && \
    chown -R kibana:kibana /opt/kibana \

ENV PATH /opt/kibana/bin:$PATH

EXPOSE 5601

USER kibana
