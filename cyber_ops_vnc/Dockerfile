FROM tjoconnor/cyber_ops as base

ARG KALI_METAPACKAGE=core
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update
RUN apt-get -y upgrade
RUN apt-get -y install kali-linux-${KALI_METAPACKAGE}
RUN apt-get -y install kali-tools-top10
RUN apt-get clean

# Install kali desktop with novnc
ARG KALI_DESKTOP=xfce
RUN apt-get -y install kali-desktop-${KALI_DESKTOP}
RUN apt-get -y install tightvncserver dbus dbus-x11 novnc net-tools

ENV USER kali
ENV VNCEXPOSE 1
ENV VNCPORT 5900
ENV VNCPWD password
ENV VNCDISPLAY 1920x1080
ENV VNCDEPTH 16
ENV NOVNCPORT 8080

# add kali user
ARG USERNAME=$USER
ARG USER_UID=1000
ARG USER_GID=$USER_UID
RUN apt-get install sudo -y

# Create the user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

USER $USER
WORKDIR /home/kali/
RUN sudo usermod --shell /bin/zsh $USER
COPY config /home/$USER/.config/

USER root
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
ENTRYPOINT [ "/entrypoint.sh" ]

