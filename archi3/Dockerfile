FROM archlinux:latest
RUN pacman -Syu --noconfirm
RUN pacman -S reflector --noconfirm
RUN reflector --country 'Australia,New Zealand' --age 6 --latest 5 --protocol https --sort rate --save /etc/pacman.d/mirrorlist
RUN pacman -S --needed git base-devel --noconfirm
RUN mkdir -p /home/ls
RUN useradd ls && chown ls /home/ls
RUN git clone https://aur.archlinux.org/yay.git /home/ls/git
RUN pacman -S firefox nautilus dina-font xorg xterm xorg-xinit x11vnc xorg-server-xvfb i3  --noconfirm
RUN echo "exec i3" >> ~/.xinitrc && chmod +x ~/.xinitrc
RUN echo "exec xterm" >> ~/.xinitrc && chmod +x ~/.xinitrc
RUN chown -R ls /home/ls/
RUN usermod -aG wheel ls
RUN echo "%wheel ALL=(ALL) ALL" >> /etc/sudoers
CMD ["x11vnc", "-create", "-forever"]
