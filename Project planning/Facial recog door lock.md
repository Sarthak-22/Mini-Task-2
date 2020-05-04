### FACIAL RECOGNITION BASED DOOR LOCK USING RPi

__Problem statement__ - 
 Operating a solenoid door lock to control the lock of a door using facial recognition methods by gathering data and training our own classifier using __OpenCV__ package.
 
__Ideation__ - 

 * Data gathering for face detection __=>__ Training our recognizer => Facial recognition (positive/negative) __=>__ signal sent to Rpi __=>__ signal sent by Rpi to solenoid lock.
 
 * RPi camera would be used to click pictures for facial recongnition. Hence, we import __Picamera library__ before writing the code for classifier. 
 
 
 Components/Softwares | Feasibilty | Advantages | Disadvantages |
 ---------------------|------------|------------|---------------|
 Raspberry Pi | Cheap and easily available. However, not beginner friendly and needs some prior programming knowledge. | Uses free/open source software. It provides directly accessible processor pins as __GPIO's__. Built-in WiFi and bluetooth module. | No fuse protection on the Rpi incorrectly connection of pins can damage the board. Not as fast compared to the CPU processing speed. No built-in __ADC__ as in Arduino. |
 Rpi camera | It can be easily fitted on a buit-in connector on Rpi board. Prerequisite knowledge based on handling Picamera library is required. | It can be easily accessed in OpenCV. It is quite useful in real-time Computer Vision problems to analyze each and evefy frame. | It comes with a very short 15cm cable. It is highly sensitive to electrical interference, static electricity or physical damage.|
 OpenCV | Easily available as a Python package. However, prior experience in programming is a must. | The package already contains many pre-trained classifier on face,eyes,smile etc. It has more number of functions and better run speed than MATLAB. Performance is better than any other Computer Vision software. | A heavy prior knowledge in scientific computing is necessary for the user. A beginner in programming cannot get a proper hands-on the same. |
