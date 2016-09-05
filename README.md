## **ROSserial test in the arduino board**

###**1.Check your test enviroment (all example for Ubuntu14.04LTS & ROS Indigo)**###

**1.1 Ubuntu OS 14.04LTS+**
		ex:https://www.ubuntu-tw.org/modules/tinyd0/
		
**1.2 ROS Indigo+ installed**
		ex:http://wiki.ros.org/indigo/Installation/Ubuntu
		
**1.3 Installing and Configuring Your ROS Environment**
		ex:http://wiki.ros.org/ROS/Tutorials/InstallingandConfiguringROSEnvironment
**1.4 Install ROSSerial Package**
		ex:http://wiki.ros.org/rosserial_arduino/Tutorials/Arduino%20IDE%20Setup	
**1.5 create ROS package (ex. mega2560_test)**
		ex:http://wiki.ros.org/ROS/Tutorials/CreatingPackage 
**1.6 cooking launch file (ex. test.launch)** 
```
<?xml version="1.0"?>

<launch>
<!-- run serial node for base mega -->	
	<node pkg="rosserial_python" type="serial_node.py" name="serial_node">
    		<param name="port" value="/dev/ttyACM0"/>
    		<param name="baud" value="57600"/>
  	</node>		
```  	
###**2.Download arduino source code which has ROSserial node program.**###
ex:https://github.com/Muchun-Yen/Driving-Wheel-Hub-Motor-with-Arduino/blob/master/mega_base.ino

###**3.Executing ROS test**###

**3.1 Open Terminator key **
```
$ test.launch
```
**3.2 Check is there any error about the rosserial.**

**3.3 Change baudrate and test again	**
```
    		<param name="port" value="/dev/ttyACM1"/>
    		<param name="baud" value="1000000"/>
```
###**4 Multi-board test launch**###
**4.1. Create python files**
```
cp ~/catkin_ws/src/rosserial/rosserial_python/nodes/serial_node.py ~/catkin_ws/src/rosserial/rosserial_python/nodes/serial_node1.py 
```
	
**4.2.modified the test launch (ex. test2boards.launch)
```
<?xml version="1.0"?>

<launch>
<!-- run serial node for base mega -->	
	<node pkg="rosserial_python" type="serial_node.py" name="serial_node">
    		<param name="port" value="/dev/ttyACM0"/>
    		<param name="baud" value="57600"/>
  	</node>
	<node pkg="rosserial_python" type="serial_node1.py" name="serial_node1">
    		<param name="port" value="/dev/ttyACM1"/>
    		<param name="baud" value="1000000"/>
  	</node>
  	
</launch>			
```
**4.3 Check is there any error about the rosserial.**
	