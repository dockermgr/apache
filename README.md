## 👋 Welcome to apache 🚀  

Apache httpd server  
  
  
## Requires scripts to be installed  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 systemmgr --config && systemmgr install scripts  
```

## Automatic install/update  

```shell
dockermgr update apache
```

OR

```shell
mkdir -p "$HOME/.local/share/srv/docker/apache/dataDir"
git clone "https://github.com/dockermgr/apache" "$HOME/.local/share/CasjaysDev/dockermgr/apache"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/apache/dataDir/." "$HOME/.local/share/srv/docker/apache/dataDir/"
```

## via command line  

```shell
docker pull casjaysdevdocker/apache:latest && \
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-apache \
--hostname casjaysdev-apache \
-e TZ=${TIMEZONE:-America/New_York} \
-v $HOME/.local/share/srv/docker/apache/dataDir/data:/data:z \
-v $HOME/.local/share/srv/docker/apache/dataDir/config:/config:z \
-p 80:80 \
casjaysdevdocker/apache:latest
```

## via docker-compose  

```yaml
version: "2"
services:
  apache:
    image: casjaysdevdocker/apache
    container_name: apache
    environment:
      - TZ=America/New_York
      - HOSTNAME=casjaysdev-apache
    volumes:
      - $HOME/.local/share/srv/docker/apache/dataDir/data:/data:z
      - $HOME/.local/share/srv/docker/apache/dataDir/config:/config:z
    ports:
      - 80:80
    restart: always
```

## Author  

🤖 casjay: [Github](https://github.com/casjay) 🤖  
⛵ dockermgr: [Github](https://github.com/dockermgr) ⛵  
