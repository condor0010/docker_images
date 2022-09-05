FROM tjoconnor/cyber_ops as base

ENV DEBIAN_FRONTEND noninteractive

# INSTALL XFCE DESKTOP
RUN apt-get update
RUN apt-get -y install kali-desktop-xfce
RUN apt-get -y install tightvncserver dbus dbus-x11 novnc net-tools sudo

ENV USER kali
ENV VNCEXPOSE 1
ENV VNCPORT 5900
ENV VNCPWD password
ENV VNCDISPLAY 1400x900
ENV VNCDEPTH 16
ENV NOVNCPORT 8080

# ADD ``KALI`` USER
ARG USERNAME=$USER
ARG USER_UID=1000
ARG USER_GID=$USER_UID
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# LAUNCH NOVNC STARTUP
USER root
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
ENTRYPOINT [ "/entrypoint.sh" ]

