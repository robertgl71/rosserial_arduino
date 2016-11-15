## Ex 4.1 Rosserial_Arduino

We have modified the original sketch, adding a subscriber that receives a int value
that modifies the senoidal frequency.

1. frec_cb takes the data from the subscriber and changes the value of frecuency variable.
'''
void frec_cb( const std_msgs::UInt16& cmd_msg){
   frequency=cmd_msg.data; //set frequency   
}
ros::Subscriber<std_msgs::UInt16> sub("frec", frec_cb);
'''
