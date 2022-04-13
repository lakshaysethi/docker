FROM ubuntu:latest
RUN apt-get update \
    && apt-get install -y \
    xterm \
    x11vnc \
    xvfb \
    i3 \
    firefox \
    git \
    qbittorrent \
    terminator \
    vlc \   
    && echo "exec i3" >> ~/.xinitrc \
    && chmod +x ~/.xinitrc  \
    && echo "exec xterm" >> ~/.xinitrc \
    && chmod +x ~/.xinitrc 

CMD ["x11vnc", "-create", "-forever"]
