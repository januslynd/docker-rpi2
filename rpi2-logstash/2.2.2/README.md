# Logstash (RPI2)

This image builds a
[Logstash](https://www.elastic.co/products/logstash) Docker image.

## How to use it

Just to check the installation you can run logstash providing your own
configuration inline.

```shell
docker run -it com.github.januslynd/logstash:2.2.2 logstash -e 'input { stdin { } } output { stdout { } }'
```

If you need to run logstash with a configuration file, logstash.conf,
that's located in your current directory, you can use the logstash
image as follows:

```shell
docker run -it -v "$PWD":/config-dir com.github.januslynd/logstash:2.2.2 logstash -f /config-dir/logstash.conf
```