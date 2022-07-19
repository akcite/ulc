# ulc

## Boot
F10 -> UEFI  

## Power on
power never

## sudo
sudo apt update  
sudo apt install ssh geany pcmanfm net-tools

## ZscalerRootCerts
cd ZscalerRootCerts  
sudo mkdir /usr/local/share/ca-certificates/extra  
sudo cp ZscalerRootCertificate-2048-SHA256.crt /usr/local/share/ca-certificates/extra/root.cert.crt  
sudo update-ca-certificates  
cd

## Chrome
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb  
sudo apt install ./google-chrome-stable_current_amd64.deb

Chrome settings:  
Security  
Manage certificates  
Authorities  
Import

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
./scripts/dependency-manager install  
mkdir build  
cd build  
cmake -DBUILD_ARAVIS=ON ..  
make -j  
sudo make install  

Set static IP

## ROS  
http://wiki.ros.org/melodic/Installation/Ubuntu

mkdir -p ~/catkin_ws/src  
cd ~/catkin_ws/  
catkin_make

## Ouster
firefox: os-122218000386.local  
roslaunch ouster_ros ouster.launch sensor_hostname:=169.254.165.155 metadata:=/home/cv/metadata.json  
rviz rviz -f os_lidar  
rosbag record -a

## .bashrc
echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc  
echo "source /home/**user_name**/catkin_ws/devel/setup.bash" >> ~/.bashrc @@ text in purple (and bold)@@  
source ~/.bashrc
