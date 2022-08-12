FROM tjoconnor/cyber_ops as base

RUN apt-get update
RUN apt-get -y upgrade
RUN apt-get -y install kali-linux-large
RUN apt-get clean

# Install xfce desktop & vnc/ novnc stuff
RUN apt-get -y install kali-desktop-xfce
RUN apt-get -y install tightvncserver dbus dbus-x11 novnc net-tools

ENV USER root
ENV VNCEXPOSE 0
ENV VNCPORT 5900
ENV VNCPWD changeme
ENV VNCDISPLAY 1920x1080
ENV VNCDEPTH 16
ENV NOVNCPORT 8080

# Install GUI installs
RUN apt-get -y install firefox-esr chromium
RUN apt remove xfce4-power-manager -y
RUN touch /root/.hushlogin
RUN apt remove qterminal -y
RUN apt install xfce4-terminal -y

# add kali user
ARG USERNAME=kali
ARG USER_UID=1000
ARG USER_GID=$USER_UID
RUN apt-get install sudo -y

# Create the user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME
USER kali
WORKDIR /home/kali/
RUN sudo usermod --shell /bin/bash kali
COPY config /home/kali/.config/

# Entrypoint to start VNC
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
ENTRYPOINT [ "/entrypoint.sh" ]
