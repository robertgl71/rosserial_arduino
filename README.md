## Ex 4.1 Rosserial_Arduino

We have modified the original sketch, adding a subscriber that receives a int value
that modifies the senoidal frequency.

### frec_cb takes the data from the subscriber and changes the value of frecuency variable.

```
void frec_cb( const std_msgs::UInt16& cmd_msg){
   frequency=cmd_msg.data; //set frequency      
}
ros::Subscriber<std_msgs::UInt16> sub("frec", frec_cb);
```
###How to run the sketch?
1. Open a new terminal and write:
```
$ roscore 
```
2. Run the rosserial application to send Arduino messages to the rest of ROS. In a new terminal type:
```
$ rosrun rosserial_python serial_node.py "serial port"  (ex.:/dev/ttyACM1) 
```
3. Open the rqt with the name of the declared topic to see the senoidal wave. Type in a new terminal:
```
rqt_plot wave
```
4. Finally open a new terminal and send new values to Arduino:
```
$ rostopic pub frec std_msgs/UInt16 "new value"
```
