FROM com.github.mariogarcia/rpi2-java:8

ARG UID=500
ARG GID=500
ARG NIFI_VERSION=1.4.0
ARG MIRROR=https://archive.apache.org/dist

ENV NIFI_BASE_DIR /opt/nifi
ENV NIFI_HOME=$NIFI_BASE_DIR/nifi-$NIFI_VERSION \
    NIFI_BINARY_URL=/nifi/$NIFI_VERSION/nifi-$NIFI_VERSION-bin.tar.gz

# Setup NiFi user
RUN groupadd -g $GID nifi || groupmod -n nifi `getent group $GID | cut -d: -f1` \
    && useradd --shell /bin/bash -u $UID -g $GID -m nifi \
    && mkdir -p $NIFI_HOME/conf/templates \
    && chown -R nifi:nifi $NIFI_BASE_DIR

USER nifi

# Download, validate, and expand Apache NiFi binary.
RUN curl -fSL $MIRROR/$NIFI_BINARY_URL -o $NIFI_BASE_DIR/nifi-$NIFI_VERSION-bin.tar.gz \
    && echo "$(curl https://archive.apache.org/dist/$NIFI_BINARY_URL.sha256) *$NIFI_BASE_DIR/nifi-$NIFI_VERSION-bin.tar.gz" | sha256sum -c - \
    && tar -xvzf $NIFI_BASE_DIR/nifi-$NIFI_VERSION-bin.tar.gz -C $NIFI_BASE_DIR \
    && rm $NIFI_BASE_DIR/nifi-$NIFI_VERSION-bin.tar.gz \
    && chown -R nifi:nifi $NIFI_HOME

# Web HTTP Port & Remote Site-to-Site Ports
EXPOSE 8080 8181

WORKDIR $NIFI_HOME

# Startup NiFi
ENTRYPOINT ["bin/nifi.sh"]
CMD ["run"]
