FROM lopsided/archlinux-arm64v8
RUN pacman -Syu --noconfirm
RUN pacman -S --needed git base-devel --noconfirm \
    && pacman -S \
    firefox \
    python3 \
    nautilus \
    terminator \
    dina-font \
    xorg \
    xterm \
    xorg-xinit \
    x11vnc \
    xorg-server-xvfb \
    i3 \
      --noconfirm
ARG user=ls
RUN useradd --system --create-home $user \
  && echo "$user ALL=(ALL:ALL) NOPASSWD:ALL" > /etc/sudoers.d/$user
USER $user
WORKDIR /home/$user
RUN git clone https://aur.archlinux.org/yay.git \
  && cd yay \
  && makepkg -sri --needed --noconfirm \
  && yay -S rofi  code dmenu --noconfirm \
# configure i3
  && echo "exec i3" >> ~/.xinitrc && chmod +x ~/.xinitrc
CMD ["x11vnc", "-create", "-forever"]
