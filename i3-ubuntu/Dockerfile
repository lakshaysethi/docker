FROM ubuntu:latest
RUN apt-get update 
RUN apt-get install -y xterm 
RUN apt-get install -y x11vnc
RUN apt-get install -y xvfb 
RUN apt-get install -y i3 
RUN echo "exec i3" >> ~/.xinitrc && chmod +x ~/.xinitrc
RUN echo "exec xterm" >> ~/.xinitrc && chmod +x ~/.xinitrc
CMD ["x11vnc", "-create", "-forever"]
