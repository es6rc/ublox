# Steps:

* Figure out what info is needed for Autoware:
`gnss_localizer` transforms *pose info* from a [Message type](http://docs.ros.org/api/nmea_msgs/html/msg/Sentence.html) which belong to a ros package: [**NMEA_Sentence**](http://wiki.ros.org/nmea_msgs).
* Publish NMEA_Sentence in u-blox driver!
```
Node => GetParam (Config Ports) => 
```
All configurations stay same in the yaml file and parser stays the same!
Change Publish Message type
* Config params: frequency and IMU

* Enable Autoware with starting Ublox driver



## Notes

* MonVER: The product type is determined from parsing the MonVER message.
* class **gps**: Handles communication with the U-Blox Devices
* kSubscribeRate: Default subscribe Rate to u-blox messages [Hz]
