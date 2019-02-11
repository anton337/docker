#
# Ubuntu Desktop (LXDE) Dockerfile
#

# Pull base image.
FROM plumbee/nvidia-virtualgl

# Install.
RUN \
  sed -i 's/# \(.*multiverse$\)/\1/g' /etc/apt/sources.list && \
  apt-get update && \
  apt-get install -y build-essential && \
  apt-get install -y software-properties-common && \
  apt-get install -y byobu curl git htop man unzip vim wget && \
  DEBIAN_FRONTEND=noninteractive apt-get install -y lxde-core xterm tightvncserver lightdm firefox net-tools openjdk-8-jdk && \
  rm -rf /var/lib/apt/lists/*

RUN mkdir /root/.vnc/ && echo "123456" | vncpasswd -f > /root/.vnc/passwd && chmod 600 /root/.vnc/passwd

RUN sed -i '21i \ \ /etc/xdg/lxsession/LXDE/* cx,' /etc/apparmor.d/lightdm-guest-session

COPY ./webserver /root/

RUN echo "#!/bin/sh" >> /root/.vnc/xstartup && \
    echo "export XKL_XMODMAP_DISABLE=1" >> /root/.vnc/xstartup && \
    echo "/root/run2.sh > /root/.vnc/webserver.log" >> /root/.vnc/xstartup && \
    #echo "/etc/X11/Xsession" >> /root/.vnc/xstartup && \
    chmod +x /root/.vnc/xstartup

# Set environment variables.
ENV HOME /root

# Define working directory.
WORKDIR /root

# Expose ports.
EXPOSE 5901
EXPOSE 8888
EXPOSE 8088


