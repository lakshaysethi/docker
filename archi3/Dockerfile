FROM archlinux:latest
RUN pacman -Syu --noconfirm
RUN pacman -S reflector --noconfirm \
  && reflector --country 'Australia,New Zealand' --age 6 --latest 5 --protocol https --sort rate --save /etc/pacman.d/mirrorlist \
RUN pacman -S --needed git base-devel --noconfirm
RUN mkdir -p /home/ls \
&& useradd ls && chown ls /home/ls
RUN git clone https://aur.archlinux.org/yay.git /home/ls/yay
RUN pacman -S firefox python nautilus dina-font xorg xterm xorg-xinit x11vnc xorg-server-xvfb i3 dmenu  --noconfirm
RUN echo "exec i3" >> ~/.xinitrc && chmod +x ~/.xinitrc \
  && echo "exec xterm" >> ~/.xinitrc && chmod +x ~/.xinitrc
RUN chown -R ls /home/ls/ \
  && usermod -aG wheel ls \
  && echo "%wheel ALL=(ALL) ALL" >> /etc/sudoers
RUN cd /home/ls && git clone https://github.com/novnc/novnc && /home/ls/novnc/utils/novnc_proxy
CMD ["x11vnc", "-create", "-forever"]
