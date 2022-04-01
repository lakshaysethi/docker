FROM ubuntu:latest
RUN apt-get update  \
&& apt-get install -y xterm  \
&& apt-get install -y x11vnc \
&& apt-get install -y xvfb  \
&& apt-get install -y i3  \
&& apt-get install -y firefox git \
&& apt-get install -y qbittorrent \
&& echo "exec i3" >> ~/.xinitrc && chmod +x ~/.xinitrc \
&& echo "exec xterm" >> ~/.xinitrc && chmod +x ~/.xinitrc
RUN apt-get install -y terminator \
&& apt-get install -y vlc
CMD ["x11vnc", "-create", "-forever"]
