webtop have done a nice job at https://docs.linuxserver.io/images/docker-webtop


the conf i use is : 

docker run -d \
  --name=webtop \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=Pacific/Auckland \
  -e KEYBOARD=en-us-qwerty `#optional` \
  -p 3000:3000 \
  --restart unless-stopped \
  lscr.io/linuxserver/webtop:arch-i3
  
