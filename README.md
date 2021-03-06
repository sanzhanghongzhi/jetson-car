Jetson Autonomous RC Car
========================
Autonomous RC Car using ROS and Keras/TensorFlow. Inspired by JetsonHacks

<p align="center">
<img src="https://github.com/dat-ai/jetson-car/raw/master/docs/img/jetson-car.jpg" width="720">
</p>
Repository Contents
-------------------
* **`/docs`** - research papers, documents, photos related to this project
* **`/model`** - a pre-trained Keras Model file (.json and .h5) to run the car autonomously
* **`/setup`** - Firmwares for Teensy 3.2 & SparkFun IMU Sensor + Set up instructions for Jetson TK1
* **`/src`** - ROS source directory (ROS Nodes and Launch files)
* **`/utils`** - Some unittest files to make sure the car is functional
* **`/Autopilot.py`** - Demo how the Autopilot model is built
* **`/FLAGS.py`** - hyper-parameters and configurations for training
* **`/drive.py`** - Demo on how to enable Jetson run autonomously. In practice, this script is activated through ROS launch.

### System Architecture
-----------------------
<p align="center">
<img src="https://github.com/dat-ai/jetson-car/raw/master/docs/architecture.png" width="640">
</p>

### Goals:
----------
* Get hands-on experience on autonomous vehicle development.
* Understand Deep Learning concepts.
* For Fun ( I probably end up taking the car to some autonomous racing competition. We'll see).

### Dependencies:
-----------------
#### Hardwares:
1. RC Car - [RedCat Volcano EPX](https://www.amazon.com/Redcat-Racing-Electric-Volcano-Included/dp/B00HVBVNVG/ref=sr_1_2?ie=UTF8&qid=1487805887&sr=8-2&keywords=RedCat+Volcano+EPX) (stock - no mod) + [Extra battery](https://www.amazon.com/Redcat-Racing-HX-3800MH-B-Battery-7-2V-Connector/dp/B00D2539IU/ref=sr_1_1?ie=UTF8&qid=1487805956&sr=8-1&keywords=Redcat-Racing+HX-3800MH)
2. NVIDIA Jetson TK1
3. Teensy 3.2
3. Intel RealSense R200
4. Intel Network 7260 Wireless Card m-pcie
5. Ultrasonic Sensor(s)

#### Softwares:

1. Stock OS for Jetson TK1 (JetPack 21.5)
2. Grinch Kernel 21.4
3. ROS Indingo for ARM
4. Keras using TensorFlow as backend
5. TensorFlow 0.8 (this is the latest version Jetson TK1 could support now)


### Installation Guide: (To be Updated)
----------------------
 
#### Software Setup

JetsonHacks provides many helpful scripts to automate the process. I will avoid to reproduce his wonderful works.

 1. Install [JetPack 21.5](https://developer.nvidia.com/embedded/jetpack) (Ubuntu + CUDA 6.5 + cuDNN v2 + OpenCV4Tegra)
 2. Install [postFlash](https://github.com/jetsonhacks/postFlash) (Enabled USB 3.0, some helpful tools for development) 
 3. Install [grinch Kernel](http://www.jetsonhacks.com/2015/05/26/install-grinch-kernel-for-l4t-21-3-on-nvidia-jetson-tk1) (allow to have more driver options)
 4. Install [ROS Indigo & Teensy Driver for Jetson TK1](https://raw.githubusercontent.com/dat-ai/jetson-car/master/setup/tk1_ros_setup.sh) - Run this script on TK1
 5. Clone this repo and set up ROS workspace
 
```shell
# Clone the repo
cd ~
git clone https://github.com/dat-ai/jetson-car

# Set up standard ROS workspace
cd jetson-car/src/
catkin_init_make
cd ..
catkin_make
```

 6. Set up ROS environment
```shell
# Add this line to the end of ./.bashrc file
source jetson-car/devel/setup.bash
```

#### Hardware Setup

##### 1. Install Teensy Driver
##### 2. Install IMU Razor 9DoF

### Test AutoPilot
------------------

* Open a new terminal
```shell
roscore
```

* Open another new terminal
```shell
roslaunch jetson_joystick jetson_joystick.launch
```

* Activate Autopilot
```shell
cd jetson-car
# Load pre-train model and drive autonomously
python drive.py model/cnn.json
```

### Author(s):
--------------
* [**Dat Nguyen**](https://github.com/dat-ai)
* I am very happy if anyone would like to work with me on this project. please shoot me an email at tdat.nguyen93@gmail.com

### Acknowledgements:
---------------------
* [JetsonHacks](http://www.jetsonhacks.com/) website provides helpful tips and tricks to work with Jetson TK1. JetsonHacks nicely simplifies the installation process with many ready-to-use scripts
* [DuckieTown](http://duckietown.mit.edu), an MIT Course,  is a great place to learn about developing autonomous vehicles.
* UPenn F1/10 Tutorials give a nice introduction to ROS, Hardware installation, and System Architecture for RC Car.
