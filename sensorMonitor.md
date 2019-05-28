[Go to Main](readme.md)
# Coil Heater Temperature Control Software

* Sensor
  - Temperature and Humidity sensor(HT-01D)
  - Heat Module - 12V
  
* Tool 
  - Visual Studio 2010, VC++/MFC
  - Atmel Studio 7
  - Atmega128
  - ISP Programmer
  - RS-232C Communication
  - I2C Interface logic by Software

This one use a ATMEL Atmega128 8bit mcu. In this project I used 12 temperature sensors same time. Actually Atmega128 support only 3 i2c channels. It use i2c function that implemented by software. The MCU communicate with zigbee wireless modules, periodically report temperature and humidity to the host computer. The host computer gathers information will be display their informations.
The host software will be control the devices automatically.

![Image](/images/SensorMonitorBD.png)

![Image](/images/TSM.PNG)
