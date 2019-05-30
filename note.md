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

### Autoware Interfaces and message type


Autoware interfaces require GNSS message type to be [**NMEA_Sentence**](http://wiki.ros.org/nmea_msgs),(`nmea2tfpose_core.cpp` in `nmea2tfpose`) There are four sub-message types: `QQ``, $PASHR`, `$GPGGA`, and `$GPRMC`. They are all **nmea/sentences** but contains different information. \
`QQ` and `$PASHR` provides with `roll, pitch, and yaw`.\
Autoware parses `Latitude, Longitude, and Height` info from `$GPGGA` and `$GPRMC`.

### Msgs

* `QQ`: contains `time_stamp`, `roll`, `pitch` and `yaw`.
* `$PASHR`: [Inertial Attitude Data](https://docs.novatel.com/OEM7/Content/SPAN_Logs/PASHR.htm), contains `time_stamp`, `roll`, `pitch` and `yaw`.
* `$GPRMC`: [Recommended minimum specific GPS/Transit data](https://docs.novatel.com/OEM7/Content/Logs/GPRMC.htm?tocpath=Logs%7CView%20Logs%7CGNSS%20Logs%7C_____59), contains `time_stamp`, `lat`, `long` and `height`.
* `$GPGGA`: [Global Positioning System Fix Data](https://docs.novatel.com/OEM7/Content/Logs/GPGGA.htm), contains `time_stamp`, `lat`, `long` and `height`.

