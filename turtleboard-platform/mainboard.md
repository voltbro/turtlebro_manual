# Mainboard

## Board design(?)

![](../.gitbook/assets/assets\_-LWqHZF8ywsK\_MiMxnHa\_-LYkSdZ3JLMo4EZbyHj5\_-LYkx2RxGkBBMZ\_SHMih\_board-manual001.png)

## Onboard buttons descriprion

`restart` Pressing this button restarts the STM32 MCU program. Rosparam values start to update, while IMU, odometry, current speed values are being reset. This button is intented for robot reconfiguration when changing rosparam values. Restart takes about 30s.

`stop` Pressing this button resets cmd\_vel values (robot stops), odometry and IMU sensor. Thats useful for manual robot repositioning at the working environment.

`hw_reset` Resets all the robot systems, including MCU and raspberry.

`reset` Resets Arduino module.

`EMRG` Terminals for Emergency Plug connection. Should be shorted in working mode.
