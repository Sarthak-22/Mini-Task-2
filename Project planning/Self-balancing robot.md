### SELF BALANCING ROBOT

__1.__   __Problem Statement__ - 
Building a self-balanced two wheel robot using a PIC32 microcontroller and a PID controller to maintain its balance.

__2.__   __Ideation__ - 
* __Hardware overview__ :

  Data from accelerometer and gyroscope in [IMU](https://en.wikipedia.org/wiki/Inertial_measurement_unit) passes to the microcontroller over I2C.

  Motors are brushless and have internal controllers that work with a pulse-width modulation (PWM) input, meaning the microcontroller can plug into them directly and control velocity using a PWM output and direction with a separate line.
  
  The motors also include built-in encoder that provides a feedback pulse output to allow us to keep track of how fast the wheels are spinning.
  
* __Software overview__ :

  Divided into 4 components - an interrupt service routine to update the PWM signal sent to the motors, a thread for reading and filtering the IMU values, a thread for reading and updating [PID](https://en.wikipedia.org/wiki/PID_controller) coefficient values.
  PID, namely the proportional-integral-derivative controller, is an extremely effective control algorithm based around a feedback loop used to control the balance of the robot. The job of a PID loop is to continously sense the input from IMU(pitch angle) , process it and send a PWM pulse signal to the motor for the rotation of the wheel.
  
  The basic working mechanism of the robot - 
  
  ![image](https://people.ece.cornell.edu/land/courses/ece4760/FinalProjects/f2018/amm452_fb262/amm452_fb262/amm452_fb262/images/overview_controlLoop.png)
  
  Components | Feasibility | Advantages | Disadvantages
  -----------| ----------- | ---------- | -------------
  Inertial Measurement Unit (IMU) | __MPU 6050__ (IMU) is readily available and no special prerequisite knowledge | Includes both accelerometer and gyroscope. Uses I2C communication. Connections can be made by simply referring to the data sheet | It is a bit noisy and drifts and not perfectly accurate | 
  Brushless Motors | Any beginnner can work with motors. Easily available | Less noisy as compared to other DC motors. They also with come with an in-built motor driver system | Cannot be used for heavy robot applications. Motor torque is generally less for larger deviation from equilibrium |
  Power Source | Easy fixation and cheap | 12V battery can easily power the motor with a nominal capacity. Long-lasting and rechargeable. | Added weight of the battery may harm the robot performance. |
  PIC32 Microcontroller | Not so easy to program. A skilled programmer required. | Cheap and readily available. Very easy to program if its use is clear. | Beginners cannot easily program. Even the datasheets are company specific. |
  
__Scope of improvement__ - 
 * More powerful motors can be used to generate better motor torque. Powerful motors would allow our robot to recover to equilibrium much more easily, and would greatly increase the range of angles from which it can succesfully recover. Although these motors would be relatively costlier as compared to normal motors but are quite reasonable according to current market standards.
 
 * A single PID loop currently takes in the pitch angle and outputs a PWM value for the wheel. We could modify this system by adding a second PID loop, so that the first outputs a desired RPM value instead, and this second PID loop takes this value and the wheel's actual RPM as input, and tries to match them by outputting some PWM value. This would make the robot more resistant to any changes to the surface it's on, or changes to its weight. For example, if we add a book on top of the robot, its RPM will be much lower than normal if its PWM is not adjusted, so the previous PID values that worked for the robot may not work with the added mass.
 
 * Another potential improvement would be to add a third PID loop that takes as input a target robot speed and the mean RPM between the two motors, and outputs an angle value. This would allow us to tell the robot to move at a certain speed, it would then attempt to lean over at a certain angle which will result in it moving at some speed in order to maintain balance. This would allow the robot to move forwards and backwards.
 
 * __However, as the number of PID loops increases, the computational efficiency and calculation time would eventually decrease. Hence, it becomes increasingly necessary to choose limited number of PID loops at a time__. 
  
Project description can be found here - [Self balancing Robot](https://github.com/Sarthak-22/Mini-Task-1/blob/master/Robotics%20Project/Self-balancing%20robot.md)
 
