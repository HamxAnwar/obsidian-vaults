FROM osrf/ros:noetic-desktop-full

RUN sudo apt-get update \
&& sudo apt-get upgrade -y \
&& sudo apt-get install -y \
nano \
git \
python3-pip \
&& rm -rf /var/lib/apt/lists/*

ARG USERNAME=hamza
ARG USER_UID=1000
ARG USER_GID=$USER_UID

#Create a non-root user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd -s /bin/bash --gid $USER_GID --uid $USER_UID -m $USERNAME \
    && mkdir /home/$USERNAME/.config && chown $USER_UID:$USER_GID /home/$USERNAME/.config 

#Setup sudo
RUN mkdir -p /etc/sudoer.d \
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoer.d/$USERNAME\
    && chmod 0440 /etc/sudoer.d/$USERNAME \
    && rm -rf /var/lib/apt/lists/*

#Add user to the dialout group
RUN usermod -aG dialout ${USERNAME}

#Copy the entrypoint to the given variable below
COPY entrypoint.sh /entrypoint.sh

#Set the entrypoint
ENTRYPOINT ["/bin/bash", "/entrypoint.sh"]

#Set the default command
CMD ["bash"]

#Container starts with the last set user, in this case hamza
USER hamza


