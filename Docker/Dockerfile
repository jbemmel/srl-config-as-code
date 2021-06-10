FROM registry.srlinux.dev/pub/srlinux:latest

COPY 42_sr_copy_custom_appmgr.sh /opt/srlinux/bin/bootscript/

# Install pyGNMI client library and Jinja2
RUN sudo yum install -y python3-pip gcc-c++ && source /opt/srlinux/python/virtual-env/bin/activate && \
    sudo python3 -m pip install pip --upgrade && sudo python3 -m pip install pygnmi jinja2

# RUN sudo mkdir -p /etc/opt/srlinux/appmgr/ && sudo cp /home/appmgr/* /etc/opt/srlinux/appmgr/

# --chown=srlinux:srlinux
# COPY ./appmgr/ /etc/opt/srlinux/appmgr/ # doesn't stick
COPY ./appmgr/ /home/appmgr

# Using a build arg to set the release tag, set a default for running docker build manually
ARG SRL_AUTO_CONFIG_RELEASE="[custom build]"
ENV SRL_AUTO_CONFIG_RELEASE=$SRL_AUTO_CONFIG_RELEASE
