# About this Image

This is the Git repo of the runtime environment Docker image for FineBI，Based on JDK8 and Tomcat 8.5, without webroot content.

# How to use

Shell:

```shell
$ docker run -d -p 8080:8080 -v /path/to/webroot:/usr/local/tomcat/webapps/webroot \
        --name finebi aniven/finebi-tomcat-env:8.5
```

Example using docker-compose.yml:

```yaml
version: '2'
services:
  finebi:
    container_name: finebi
    image: aniven/finebi-tomcat8-env:8.5
    restart: unless-stopped
    ports:
      - "8080:8080"
    volumes:
      - ./webroot:/usr/local/tomcat/webapps/webroot
    network_mode: bridge
```

After the container is running normally, Copy the FineBI application file to the host directory of the container volume mapping, Then restart the container.

Open the URL in browser: <http://{host-ip}:8080/webroot/decision>

