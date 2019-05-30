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

* `nmea2tfpose_core.cpp` in `autoware/ros/src/computing/perception/localization/packages/gnss_localizer/nodes/nmea2tfpose` parses 4 message type from  [**NMEA_Sentence**](http://wiki.ros.org/nmea_msgs), which are 
<p align="center">
<b>`QQ`: contains `time_stamp`, `roll`, `pitch` and `yaw`</b> <br>
<b>`$PASHR`: Inertial Attitude Data, contains `time_stamp`, `roll`, `pitch` and `yaw`</b>
<b>`$GPRMC`: Recommended minimum specific GPS/Transit data, contains `time_stamp`, `lat`, `long` and `height`</b>
<b>`$GPGGA`: Global Positioning System Fix Data, contains `time_stamp`, `lat`, `long` and `height`</b>
</p>
