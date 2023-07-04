## 👋 Welcome to readarr 🚀  

readarr README  
  
  
## Install my system scripts  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 sudo systemmgr --config && sudo systemmgr install scripts  
```
  
## Automatic install/update  
  
```shell
dockermgr update readarr
```
  
## Install and run container
  
```shell
mkdir -p "$HOME/.local/share/srv/docker/readarr/rootfs"
git clone "https://github.com/dockermgr/readarr" "$HOME/.local/share/CasjaysDev/dockermgr/readarr"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/readarr/rootfs/." "$HOME/.local/share/srv/docker/readarr/rootfs/"
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-readarr \
--hostname readarr \
-e TZ=${TIMEZONE:-America/New_York} \
-v $HOME/.local/share/srv/docker/casjaysdevdocker-readarr/rootfs/data:/data:z \
-v $HOME/.local/share/srv/docker/casjaysdevdocker-readarr/rootfs/config:/config:z \
-p 80:80 \
casjaysdevdocker/readarr:latest
```
  
## via docker-compose  
  
```yaml
version: "2"
services:
  ProjectName:
    image: casjaysdevdocker/readarr
    container_name: casjaysdevdocker-readarr
    environment:
      - TZ=America/New_York
      - HOSTNAME=readarr
    volumes:
      - $HOME/.local/share/srv/docker/casjaysdevdocker-readarr/rootfs/data:/data:z
      - $HOME/.local/share/srv/docker/casjaysdevdocker-readarr/rootfs/config:/config:z
    ports:
      - 80:80
    restart: always
```
  
## Get source files  
  
```shell
dockermgr download src casjaysdevdocker/readarr
```
  
OR
  
```shell
git clone "https://github.com/casjaysdevdocker/readarr" "$HOME/Projects/github/casjaysdevdocker/readarr"
```
  
## Build container  
  
```shell
cd "$HOME/Projects/github/casjaysdevdocker/readarr"
buildx 
```
  
## Authors  
  
🤖 casjay: [Github](https://github.com/casjay) 🤖  
⛵ casjaysdevdocker: [Github](https://github.com/casjaysdevdocker) [Docker](https://hub.docker.com/u/casjaysdevdocker) ⛵  
