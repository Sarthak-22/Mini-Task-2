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
 
__Scope of improvement/changes__ -

 * Since the Rpi camera comes with a short cable, it is possible to buy reasonable third party cables with lengths between 5cm-1m. This will help the camera to be portable and flexible to use. 

* The facial recognition system does not work well in dark or places with less light intensity. Hence, as a possible solution, we can connect an LED, photoresistor and a motion sensor to the control system and program it in such a way that LED glows only when the motion sensor senses movement and the light intensity is less then a certain threshold level. The rate of these cables is quite subsidised and is easily available. 

* Another problem is that our algorithm can also detect faces from pictures — for instance, someone can unlock it by showing a picture from his mobile phone. We can improve the above issue by training our own [cascade classifier](https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_objdetect/py_face_detection/py_face_detection.html). We can train this classifier by gathering a training set of approximately 20-30 pictures of the face. 

* Since all the circuit components, including the solenoid door lock, are powered by electricity, there is a high risk of the door lock not operating in case of a power failure. Hence, as a modification to the above issue, we can connect a backup power supply in form of a mini generator or a battery to resume the performance of door lock.

* All the other components/softwares and their uses have been well defined in the above project and require no further modifications.

The Project description can be found here - [Facial Recog based Door lock]()
