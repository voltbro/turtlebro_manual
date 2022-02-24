# Services available

Rosserial lib provides following services to control the mainboard.

## /reset service

Service call resets odometry ( `/odom` ) and current velocity setpoint ( `/cmd_vel` ). Robot stops and resets its position info. Service call accepts no parameters. \


{% hint style="info" %}
If one moves robot after /reset call it can be seen that odometry data is non-zero, although wheels did not spin. That happens because robot uses IMU data to calculate its position.
{% endhint %}

## /set\_pid service

Service sets PID values for motor control algorithm. Message type is `turtlebro/PidRegulator`\


```
float32 Ki
float32 Kp
float32 Kd
---
bool status
```

## /board\_info service&#x20;

Service provides data on firmware version and MCU unique serial number

> ```
> mcu_id:
>   data: "0025001D3148501020333044"
> firmware_version:
>   data: "0.1_c32cfe6"
> ```

## /start\_motor service

Service starts LIDAR rotation ( RPLidar ). No parameters needed.&#x20;

## /stop\_motor service

Service stops LIDAR rotation ( RPLidar ). No parameters needed.&#x20;
