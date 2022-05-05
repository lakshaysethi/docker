FROM archlinux:latest
ARG user=ls
# update system
RUN pacman -Syu --noconfirm && \
  pacman -S --needed git base-devel --noconfirm && \
# Install yay and make a sudo user
  useradd --system --create-home $user \
  && echo "$user ALL=(ALL:ALL) NOPASSWD:ALL" > /etc/sudoers.d/$user
USER $user
WORKDIR /home/$user
RUN git clone https://aur.archlinux.org/yay.git \
  && cd yay \
  && makepkg -sri --needed --noconfirm \
  && sudo pacman --noconfirm -S firefox \ 
  && sudo pacman --noconfirm -S python3  \ 
  && sudo pacman --noconfirm -S thunar \ 
  && sudo pacman --noconfirm -S baobab \ 
  && sudo pacman --noconfirm -S terminator  \ 
  && sudo pacman --noconfirm -S dina-font  \ 
  && sudo pacman --noconfirm -S xorg  \ 
  && sudo pacman --noconfirm -S xterm  \ 
  && sudo pacman --noconfirm -S xorg-xinit  \ 
  && sudo pacman --noconfirm -S x11vnc   \
  && sudo pacman --noconfirm -S xorg-server-xvfb \
  && sudo pacman --noconfirm -S i3  \
  && sudo pacman --noconfirm -S code \
  && yay -S rofi --noconfirm \
# configure i3
  && echo "exec i3" >> ~/.xinitrc && chmod +x ~/.xinitrc
CMD ["x11vnc", "-create", "-forever"]
