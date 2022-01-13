FROM archlinux:latest
RUN pacman -Syu --noconfirm
RUN pacman -S reflector --noconfirm && reflector --country 'Australia,New Zealand' --age 6 --latest 5 --protocol https --sort rate --save /etc/pacman.d/mirrorlist
RUN pacman -S git --noconfirm && git clone https://github.com/novnc/novnc /home/novnc
CMD ["/home/novnc/utils/novnc_proxy", "--vnc", "arch:5900"]
