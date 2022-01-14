FROM archlinux:latest
# update system
RUN pacman -Syu --noconfirm
# download required packages
RUN pacman -S --needed git base-devel --noconfirm

# Install yay and make a sudo user
ARG user=ls
RUN useradd --system --create-home $user \
  && echo "$user ALL=(ALL:ALL) NOPASSWD:ALL" > /etc/sudoers.d/$user
USER $user
WORKDIR /home/$user
RUN git clone https://aur.archlinux.org/yay.git \
  && cd yay \
  && makepkg -sri --needed --noconfirm
# update mirrors
RUN sudo pacman -S reflector --noconfirm && sudo reflector --country 'Australia,New Zealand' --age 6 --latest 5 --protocol https --sort rate --save /etc/pacman.d/mirrorlist
RUN sudo pacman -S firefox python3 nautilus terminator dina-font xorg xterm xorg-xinit x11vnc xorg-server-xvfb i3   --noconfirm
RUN yay -S rofi gitahead-bin --noconfirm
# configure i3
RUN echo "exec i3" >> ~/.xinitrc && chmod +x ~/.xinitrc
CMD ["x11vnc", "-create", "-forever"]
