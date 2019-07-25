FROM archlinux/base:latest

#  Change source address

# Update package info
RUN pacman -Sy --noconfirm
RUN pacman -S git base-devel --noconfirm --needed

# Create build user
RUN useradd -m builduser 
RUN echo "builduser ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/notroot

USER builduser
WORKDIR /home/builduser

# Install trizen
RUN git clone https://aur.archlinux.org/trizen-git.git && cd trizen-git && makepkg --noconfirm -si

# Install vcpkg
RUN trizen -S vcpkg-git --noconfirm
