# GROOVYSERV (RPI2)

This Docker image executes a `groovyserver` instance and exposes
`groovyclient` in the user's available `$PATH`.To build this image,
once you are in the `rpi-java` directory you have to:

- Execute `./build.sh`
- Geckodriver needs to open firewall to connections comming from same
  ip (Need to know how to narrow this)
