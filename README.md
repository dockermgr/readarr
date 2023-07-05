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
-e PUID=1000 \
-e PGID=1000 \
-v /mnt/books:/books:z \
-v /mnt/downloads:/downloads:z \
-v $HOME/.local/share/srv/docker/casjaysdevdocker-readarr/rootfs/config:/config:z \
-p 0.0.0.0:8787:8787 \
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
      - PUID=1000
      - PGID=1000
    volumes:
      - /mnt/books:/books:z
      - /mnt/downloads:/downloads:z
      - $HOME/.local/share/srv/docker/casjaysdevdocker-readarr/rootfs/config:/config:z
    ports:
      - 0.0.0.0:8787:8787
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
