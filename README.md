# ULC

## Boot
F10 -> UEFI  
F2 -> BIOS

## Power on
power never

## sudo
sudo apt update  
sudo apt install ssh geany pcmanfm net-tools git gitk terminator  

## akcite/ulc
cd && mkdir src && cd src && git clone https://github.com/akcite/ulc  

## Chrome
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb  
sudo apt install ./google-chrome-stable_current_amd64.deb

Chrome settings:  
Security  
Manage certificates  
Authorities  
Import

## ZscalerRootCerts
cd ZscalerRootCerts  
sudo mkdir /usr/local/share/ca-certificates/extra  
sudo cp ZscalerRootCertificate-2048-SHA256.crt /usr/local/share/ca-certificates/extra/root.cert.crt  
sudo update-ca-certificates  
cd

## ROS  
http://wiki.ros.org/melodic/Installation/Ubuntu

mkdir -p ~/catkin_ws/src  
cd ~/catkin_ws/  
catkin_make

## Apriltag  
git clone https://github.com/AprilRobotics/apriltag  
cd apriltag  
mkdir build  
cd build  
cmake ..  
make -j  
sudo make install

## TIS  
git clone https://github.com/TheImagingSource/tiscamera    
cd tiscamera  
git checkout baacb4cfaa7858c2e6cfb4f1a297b404c4e002f6  
./scripts/dependency-manager install  
mkdir build  
cd build  
cmake -DBUILD_ARAVIS=ON ..  
make -j  
sudo make install  

Set static IP

**tcam-gigetool**  
https://www.theimagingsource.com/documentation/tiscamera/tcam-gigetool.html  
tcam-gigetool list  
tcam-gigetool info ####  
tcam-gigetool set --mode dhcp ####  
tcam-gigetool set --mode static ####  

## Pangolin
sudo apt install -y libglew-dev  

cd ~/src  
git clone https://github.com/stevenlovegrove/Pangolin.git  
cd Pangolin  
git checkout ad8b5f83222291c51b4800d5a5873b0e90a0cf81  
mkdir build && cd build  
cmake \  
    -DCMAKE_BUILD_TYPE=Release \  
    -DCMAKE_INSTALL_PREFIX=/usr/local \  
    ..  
make -j4  
sudo make install  

## Velodyne
http://wiki.ros.org/velodyne/Tutorials/Getting%20Started%20with%20the%20Velodyne%20VLP16  

1. static IP  
2. sudo apt-get install ros-melodic-velodyne  
3. cd ~/catkin_ws/src/ && git clone https://github.com/ros-drivers/velodyne.git  
4. cd ..  
5. rosdep install --from-paths src --ignore-src --rosdistro melodic -y  
6. catkin_make

	roslaunch velodyne_pointcloud VLP16_points.launch  
	rosrun rviz rviz -f velodyne  
	rosrun tf static_transform_publisher 0 0 0 0 0 0 1 map velodyne 10  

default velodyne IP: 192.168.1.201  

## Velodyne dual  

**Dual Lidar**  "hgrw commented on May 7, 2019"  
https://github.com/ros-drivers/velodyne/issues/108

roslaunch velodyne_pointcloud VLP16_dual.launch  
rviz rviz  
rosrun tf static_transform_publisher 0 0 0 0 0 0 1 map vlp201 10  
rosrun tf static_transform_publisher 0 0 0 0 0 0 1 map vlp202 10  

## Ouster
firefox: os-122218000386.local  
roslaunch ouster_ros ouster.launch sensor_hostname:=169.254.165.155 metadata:=/home/cv/metadata.json  
rviz rviz -f os_lidar  
rosbag record -a

## .bashrc
echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc  
echo "source /home/**user_name**/catkin_ws/devel/setup.bash" >> ~/.bashrc  
source ~/.bashrc

## Memo

https://static.ouster.dev/sensor-docs/image_route1/image_route2/common_sections/API/tcp-api.html  

Would you be able to run the following command utilizing the TCP API and send me the results:  
nc 122218000386.local 7501  
get_telemetry  

## git

[user]  
        name = Guoxuan Zhang  
        email = guoxuan.zhang@spx.com  
[alias]  
        acm = !git add -A && git commit -m  
        co = checkout  
        ci = commit  
        st = status  
        br = branch  
        hist = log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short  
        type = cat-file -t  
        dump = cat-file -p  
        rh = reset --hard  
        rl = !git ls-tree --full-tree -r HEAD  

  

## image_view

roslaunch tcam_publish tcam_publish.launch cam_name:=cam_front cam_serial:=#38810013  
rosrun image_view image_view image:=/cam_front_publish/image_rect  
(mouse right click, save to current folder)  


## TeamViewer
https://www.teamviewer.com/en/download/linux  
sudo apt install ./teamviewer_15.32.3_amd64.deb 

