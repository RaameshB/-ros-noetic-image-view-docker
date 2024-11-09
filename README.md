### NOTE: This has been built on ARM and probably only will work with ARM CPUs.
## Description
This is a ROS Noetic docker image with [image_view](http://wiki.ros.org/image_view) installed and set up.
## Getting started
Pull the docker image
```bash
docker pull ghcr.io/raameshb/ros-noetic-image-view
```
Run the docker image
```bash
docker run -it \
    --network host \
    --env DISPLAY=$DISPLAY \
    --env XAUTHORITY=/home/$USER/.Xauthority \
    --volume /tmp/.X11-unix:/tmp/.X11-unix \
    --volume /home/$USER/.Xauthority:/home/pearl/.Xauthority \
    --privileged ghcr.io/raameshb/ros-noetic-image-view
```
Alternatively, run the docker image with the camera view already running
```bash
docker run -it \
    --network host \
    --env DISPLAY=$DISPLAY \
    --env XAUTHORITY=/home/$USER/.Xauthority \
    --volume /tmp/.X11-unix:/tmp/.X11-unix \
    --volume /home/$USER/.Xauthority:/home/pearl/.Xauthority \
    --privileged \
    ghcr.io/raameshb/ros-noetic-image-view rosrun image_view image_view image:=[NAME_OF_ROSTOPIC]
```
For example, to use with the [libcamera ROS driver](https://github.com/ctu-mrs/libcamera_ros_driver) (I also have a [docker image](https://github.com/RaameshB/libcamera-ros-driver-docker/pkgs/container/libcamera-ros-driver) for this repo) run
```bash
docker run -it \
    --network host \
    --env DISPLAY=$DISPLAY \
    --env XAUTHORITY=/home/$USER/.Xauthority \
    --volume /tmp/.X11-unix:/tmp/.X11-unix \
    --volume /home/$USER/.Xauthority:/home/pearl/.Xauthority \
    --privileged \
    ghcr.io/raameshb/ros-noetic-image-view rosrun image_view image_view image:=/uav1/camera_front/image_raw
```
