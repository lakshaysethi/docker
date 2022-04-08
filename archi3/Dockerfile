FROM lopsided/archlinux-arm64v8
RUN pacman -Syu --noconfirm
RUN pacman -S --needed git base-devel --noconfirm

# update mirrors
# RUN pacman -S reflector --noconfirm && reflector --country 'Australia,New Zealand' --age 6 --latest 5 --protocol https --sort rate --save /etc/pacman.d/mirrorlist
RUN pacman -S firefox \
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
  && makepkg -sri --needed --noconfirm
RUN yay -S rofi  code --noconfirm
RUN yay -S dmenu --noconfirm
# configure i3
RUN echo "exec i3" >> ~/.xinitrc && chmod +x ~/.xinitrc
CMD ["x11vnc", "-create", "-forever"]
