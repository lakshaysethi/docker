FROM ubuntu:latest
RUN apt update
RUN apt install git python -y && git clone https://github.com/novnc/novnc /home/novnc
CMD ["/home/novnc/utils/novnc_proxy", "--vnc", "host:4444"]
