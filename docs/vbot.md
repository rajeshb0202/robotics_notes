

i like to drink :tropical_drink: after i play with my robot


---
## microcontroller
- filtered velocity is off now

---
## gazebo plugins
- i have disabled the publishing of tf between the odom and the base_footprint.
- in the diff drive plugin , i have enabled the wheel_tf

---
## EKF plugins:
- map_frame is turned off


---
## udev rules for the vbot
- Lidar: /dev/rplidar
- esp32 microcontroller: /dev/esp32
- logitech webcam 1 : /dev/logi_webcam1
- logitech webcam 1 : /dev/logi_webcam2
- fisheye webcam: /dev/fisheye_usbcam



---

## interfaces

| Sim Robot- gazebo classic | **Sim Robot- gazebo Fortress** | Real robot                                               |
| ------------------------- | ------------------------------ | -------------------------------------------------------- |
|                           |                                |                                                          |
| /robot_description        | /robot_description             | /robot_description                                       |
| /joint_states             | /joint_states                  | /joint_states                                            |
| /cmd_vel                  | /cmd_vel                       | /cmd_vel    (microros side)                              |
|                           |                                | /odom                                                    |
| /scan                     | /scan                          | /scan                                                    |
| /tf                       | /tf                            | /tf                                                      |
| /tf_static                |                                | /tf_static                                               |
| /rgb_camera/image_raw     | /rgb_camera/image_raw          |                                                          |
| /rgb_camera/camera_info   | /rgb_camera/camera_info        |                                                          |
| /oakd/rgb/camera_info     |                                |                                                          |
| /oakd/rgb/image_raw       |                                | <br>                                                     |
| /oakd/right/image_raw     |                                |                                                          |
| /oakd/right/camera_info   |                                |                                                          |
| /oakd/left/image_raw      |                                |                                                          |
| /oakd/left/camera_info    |                                |                                                          |
| /oakd/depth/image_raw     |                                |                                                          |
| /oakd/depth/points        |                                |                                                          |
| /imu/data_raw             | ~~/imu~~                       | /imu/data_raw                                            |
|                           | /drift                         |                                                          |
|                           |                                | /encoder_info       (microorosside)                      |
|                           |                                | /set_wheel_velocities (for debugging)    (microros side) |
|                           |                                | /battery_voltage         (microros side)                 |
|                           |                                | /status_microcontroller         (microros side)          |
|                           |                                |                                                          |

---

## PID parameters tuning

| Kp  | KI  | Kd  | comments                                                                |
| --- | --- | --- | ----------------------------------------------------------------------- |
| 0.5 | 3.0 | 0.1 | sets quickly … di not realise any problem                               |
| 0.5 | 3.0 | 0   | sets quickly … Did not notice any change after setting Kd = 0           |
| 0.5 | 2.0 | 0   | sets quickly … Did not notice any major change after lowering Ki to 2.0 |
|     |     |     |                                                                         |



---
## encoder ticks count

|                        | right_wheel (CW)     | average | right_wheel(CCW) | average |     | left_wheel(CW) | average | leftwheel(CCW) | average |
| ---------------------- | -------------------- | ------- | ---------------- | ------- | --- | -------------- | ------- | -------------- | ------- |
| 5                      | 12395                | 2479    | 12364            | 2472    |     | 12372          | 2474    | 12453          | 2490    |
| 10                     | 24751                | 2475    | 24752            | 2475    |     | 24736          | 2473    | 24809          | 2480    |
| 15                     | 37129                | 2475    | 37130            | 2475    |     | 37106          | 2473    | 37209          | 2480    |
| 20                     | 49487                | 2474    | 49473            | 2473    |     | 49477          | 2473    | 49537          | 2476    |
|                        |                      |         |                  |         |     |                |         |                |         |
| final ticks considered | 2475 for both wheels |         |                  |         |     |                |         |                |         |
