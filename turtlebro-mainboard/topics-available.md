# Topics available

Mainboard communicates with ROS using **Publishers** and **Subscribers** via _rosserial_ lib. STM32 and Arduino do not have their own USB ports, so, to allow them to send data to ROS, TurtleBro mainboard incorporates USB-UART bridges and USB-hub, thus allowing single USB-cable to pass all the data between ROS and robot.

## /bat topic

Contains robot power supply status info, including voltages and currents. Message type is `sensor_msgs/BatteryState`

```
std_msgs/Header header
  uint32 seq
  time stamp
  string frame_id
float32 voltage
float32 current
float32 charge
float32 capacity
float32 design_capacity
float32 percentage
uint8 power_supply_status
uint8 power_supply_health
uint8 power_supply_technology
bool present
float32[] cell_voltage
string location
string serial_number
```

## /cmd\_vel topic

Robot movement control topic. Message type is `geometry_msgs/Twist` Robot starts to execute commands from this topic immediately after their publishing. Current command is executed until the reception of the next one. Thus, if you want robot to stop you have to publish zero velocity values in this topic.&#x20;

```
geometry_msgs/Vector3 linear
  float64 x
  float64 y
  float64 z
geometry_msgs/Vector3 angular
  float64 x
  float64 y
  float64 z
```

## /imu topic

Inertial Measurement Unit data topic. Contains gyroscope, accelerometer and compass measurements. Message type is `sensor_msgs/Imu`

```
std_msgs/Header header
  uint32 seq
  time stamp
  string frame_id
geometry_msgs/Quaternion orientation
  float64 x
  float64 y
  float64 z
  float64 w
float64[9] orientation_covariance
geometry_msgs/Vector3 angular_velocity
  float64 x
  float64 y
  float64 z
float64[9] angular_velocity_covariance
geometry_msgs/Vector3 linear_acceleration
  float64 x
  float64 y
  float64 z
float64[9] linear_acceleration_covariance
```

Covariance data left blank.

## /odom topic

This topic contains odometry data - information about robot position, based on the wheel traveled paths. By default, angular movement of the robot is taken from IMU sensor, while linear is based on wheels. Message type is `nav_msgs/Odometry`

```
std_msgs/Header header
  uint32 seq
  time stamp
  string frame_id
string child_frame_id
geometry_msgs/PoseWithCovariance pose
  geometry_msgs/Pose pose
    geometry_msgs/Point position
      float64 x
      float64 y
      float64 z
    geometry_msgs/Quaternion orientation
      float64 x
      float64 y
      float64 z
      float64 w
  float64[36] covariance
geometry_msgs/TwistWithCovariance twist
  geometry_msgs/Twist twist
    geometry_msgs/Vector3 linear
      float64 x
      float64 y
      float64 z
    geometry_msgs/Vector3 angular
      float64 x
      float64 y
      float64 z
  float64[36] covariance
```

## /scan topic

This topic contains LIDAR data (point cloud). Data is received through LIDAR serial interface -> USB-UART bridge -> USB-hub -> ROS. Message type is`sensor_msgs/LaserScan`

```
std_msgs/Header header
  uint32 seq
  time stamp
  string frame_id
float32 angle_min
float32 angle_max
float32 angle_increment
float32 time_increment
float32 scan_time
float32 range_min
float32 range_max
float32[] ranges
float32[] intensities
```
