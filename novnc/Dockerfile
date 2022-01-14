FROM archlinux:latest
RUN pacman -Syu --noconfirm
RUN pacman -S git python --noconfirm && git clone https://github.com/novnc/novnc /home/novnc
CMD ["/home/novnc/utils/novnc_proxy", "--vnc", "arch:5900"]
