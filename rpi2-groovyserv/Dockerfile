FROM com.github.mariogarcia/rpi2-java:8

# BUILD DEPENDENCIES
RUN pacman --noconfirm -S unzip go

ENV GROOVY_VERSION 2.4.12
ENV GROOVYSERV_VERSION 1.1.0

# GROOVY
RUN curl \
    -L  https://dl.bintray.com/groovy/maven/apache-groovy-binary-$GROOVY_VERSION.zip\
    --output /tmp/apache-groovy-binary-$GROOVY_VERSION.zip

RUN mkdir -p /opt/groovy/
RUN unzip /tmp/apache-groovy-binary-$GROOVY_VERSION.zip -d /opt/groovy/

# GROOVYSERV
RUN curl \
    -L https://bitbucket.org/kobo/groovyserv-mirror/downloads/groovyserv-$GROOVYSERV_VERSION-src.zip \
    --output /tmp/groovyserv.zip

RUN mkdir -p /opt/groovyserv/
RUN unzip /tmp/groovyserv.zip -d /tmp/
RUN cd /tmp/groovyserv-$GROOVYSERV_VERSION/ && ./gradlew clean distLocalBin
RUN unzip /tmp/groovyserv-$GROOVYSERV_VERSION/build/distributions/groovyserv-$GROOVYSERV_VERSION-bin-local.zip \
    -d /opt/groovyserv/
RUN touch /opt/groovyserv/groovyserv.txt

# ENVIRONMENT
ENV GROOVY_HOME /opt/groovy/groovy-$GROOVY_VERSION
ENV GROOVY_SERVER /opt/groovyserv/groovyserv-$GROOVYSERV_VERSION
ENV PATH $PATH:$GROOVY_HOME/bin:$GROOVY_SERVER/bin
ENV JAVA_OPTS="-Djava.security.egd=file:/dev/./urandom -Djava.awt.headless=true -Xmx256m "

# ENTRYPOINT
ENTRYPOINT ["tail", "-f", "/opt/groovyserv/groovyserv.txt"]
