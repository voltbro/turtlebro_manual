# Work with Arduino

Mainboard includes ATmega2560 MCU with tracing corresponding to Arduino Mega board to allow use of standard shields. MCU comes with Arduino bootloader preinstalled. Thus controller is out-of-box ready to launch Arduino IDE sketches.\
To work with MCU, you need to download and install Arduino IDE from [arduino.cc](https://www.arduino.cc) website. Choose Arduino Mega 2560 in Board settings.

## ROS interaction

ATmega is connected to Raspberry via Serial1 port. Service _rosserial_ on the Raspberry platform controls data exchange between ATmega and ROS. \
To connect Arduino to ROS you have to initialize ros\_lib with parameters Serial1 and 115200 baudrate as shown below

```cpp
#include <ros.h>

class NewHardware : public ArduinoHardware
{
  public:
  NewHardware():ArduinoHardware(&Serial1, 115200){};
};

ros::NodeHandle_<NewHardware>  nh;
```

You can look for examples at rosserial official documentation at [http://wiki.ros.org/rosserial\_arduino/Tutorials](http://wiki.ros.org/rosserial\_arduino/Tutorials)

## Arduino ros\_lib library

To work with Arduino throughout ROS you have to install ros\_lib library\
Download at  [https://yadi.sk/d/BcI1126boKkf-A](https://yadi.sk/d/BcI1126boKkf-A)\
New libraries install in Arduino IDE guide [https://www.arduino.cc/en/guide/libraries](https://www.arduino.cc/en/guide/libraries#)\
If you plan to use custom message you have to build ros\_lib by yourself with command\


```bash
rosrun rosserial_arduino make_libraries.py
```

and then move it to Arduino libraries folder

## Arduino features

Forward part of mainboard includes two buttons connected to D23 and D24 pins and two switches connected to D22 and D25. To read them use function `digitalRead(pin)`Between switches there are four LEDs connected to D26, D27, D28 and D29 pins.\
Left side of the platform has three headers for use with servos - D44, D45 and D46.\


{% hint style="warning" %}
WARNING! Servo headers are powered up by dedicated power supply capable of providing 4 Amps at 5 Volts. In no case these power pins can be connected to other pins of mainboard!
{% endhint %}

## RGB LEDs stripe

Under the board, there are 24 RGB LEDs of the WS2812 model. We advise to use [FastLED library](https://github.com/FastLED/FastLED) to control this LED stripe. Controlling pin is D30.
