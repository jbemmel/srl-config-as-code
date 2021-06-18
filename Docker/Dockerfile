FROM registry.srlinux.dev/pub/srlinux:latest

COPY 42_sr_copy_custom_appmgr.sh /opt/srlinux/bin/bootscript/

# Install pyGNMI and Jinja2 to /usr/local/lib/python3.6/site-packages
RUN sudo yum install -y python3-pip gcc-c++ && \
    sudo python3 -m pip install pip --upgrade && \
    sudo python3 -m pip install pygnmi jinja2 nsenter \
      --target /opt/srlinux/python/virtual-env/lib/python3.6/site-packages/

# Update PYTHONPATH to include our custom packages
# RUN sudo sed -i 's|export PATH=/usr/sbin:$PATH|export PATH=/usr/sbin:$PATH;export PYTHONPATH=/usr/local/lib/python3.6/site-packages:$PYTHONPATH|g' /opt/srlinux/bin/sr_cli

# RUN sudo mkdir -p /etc/opt/srlinux/appmgr/ && sudo cp /home/appmgr/* /etc/opt/srlinux/appmgr/

# --chown=srlinux:srlinux
# COPY ./appmgr/ /etc/opt/srlinux/appmgr/ # doesn't stick
COPY ./appmgr/ /home/appmgr

# Using a build arg to set the release tag, set a default for running docker build manually
ARG SRL_AUTO_CONFIG_RELEASE="[custom build]"
ENV SRL_AUTO_CONFIG_RELEASE=$SRL_AUTO_CONFIG_RELEASE
