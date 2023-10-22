FROM osrf/ros:noetic-desktop-full

RUN apt-get update \
&& apt-get upgrade -y \
&& apt-get install -y \
nano \
git \
python3-pip \
curl \
python3-catkin-tools \
ros-noetic-camera-info-manager \
ros-noetic-image-view
RUN rm -rf /var/lib/apt/lists/*

#Make thesis workspace
RUN mkdir -p /root/ros_thesis
WORKDIR /root/ros_thesis

#Modify the .bashrc file in the container.
RUN echo 'source /opt/ros/noetic/setup.bash' >> /root/.bashrc
RUN echo 'source /root/ros_thesis/event_ws/devel/setup.bash' >> /root/.bashrc

#Set the default command
CMD ["bash"]