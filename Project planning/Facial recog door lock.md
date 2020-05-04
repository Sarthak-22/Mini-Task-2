### FACIAL RECOGNITION BASED DOOR LOCK USING RPi

__Problem statement__ - 
 Operating a solenoid door lock to control the lock of a door using facial recognition methods by gathering data and training our own classifier using __OpenCV__ package.
 
__Ideation__ - 

 * Data gathering for face detection __=>__ Training our recognizer => Facial recognition (positive/negative) __=>__ signal sent to Rpi __=>__ signal sent by Rpi to solenoid lock
 * RPi camera would be used to click pictures for facial recongnition. Hence, we import __Picamera library__ before writing the code for classifier. 
