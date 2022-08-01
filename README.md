# istall-ross
i istall ros in ubuntu and in jetson nano
How to install Ros on the Justin Nano
Search for xubuntu20.04 Focal Fossa

Download Xubuntu 20.04 Focal Fossa L4T R32.3.1 download xubntu

open zip file

Search your browser for balenaEtcher

downloading programs

Open the program and click on flash from file

Select image disk file and then flash

Blina has done

System configuration

Configure the program (language - internet - region - account creation (name - personal name - password) - website)
Open the program with the assigned password
Search the browser for a way to install Rose2 from the main source
Click on Debian packages
Copy the commands in the Terminal until the installation is complete.
Set locale
Make sure you have a locale which supports UTF-8. If you are in a minimal environment (such as a docker container), the locale may be something minimal like POSIX. We test with the following settings. However, it should be fine if you’re using a different UTF-8 supported locale
locale # check for UTF-8

sudo apt update && sudo apt install locales

sudo locale-gen en_US en_US.UTF-8

sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8

export LANG=en_US.UTF-8

locale # verify settings

Setup Sources
You will need to add the ROS 2 apt repositories to your system. First, make sure that the Ubuntu Universe repository is enabled by checking the output of this command.
apt-cache policy | grep universe

This should output a line like the one below: 500 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=universe,b=amd64 If you don’t see an output line like the one above, then enable the Universe repository with these instructions.
sudo apt install software-properties-common

sudo add-apt-repository universe

Now add the ROS 2 apt repository to your system.

sudo apt update && sudo apt install curl gnupg2 lsb-release

sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

Then add the repository to your sources list.

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

Install ROS 2 packages
Update your apt repository caches after setting up the repositories.
sudo apt update

ROS 2 packages are built on frequently updated Ubuntu systems. It is always recommended that you ensure your system is up to date before installing new packages.
sudo apt upgrade Desktop Install (Recommended): ROS, RViz, demos, tutorials. sudo apt install ros-foxy-desktop ROS-Base Install (Bare Bones): Communication libraries, message packages, command line tools. No GUI tools. sudo apt install ros-foxy-ros-base

Environment setup
Sourcing the setup script
Set up your environment by sourcing the following file.
source /opt/ros/foxy/setup.bash

Try some examples
If you installed ros-foxy-desktop above you can try some examples. In one terminal, source the setup file and then run a C++ talker:
source /opt/ros/foxy/setup.bash

ros2 run demo_nodes_cpp talker

In another terminal source the setup file and then run a Python listener:

source /opt/ros/foxy/setup.bash

ros2 run demo_nodes_py listener

You should see the talker saying that it’s Publishing messages and the listener saying I heard those messages. This verifies both the C++ and Python APIs are working properly. Hooray!
