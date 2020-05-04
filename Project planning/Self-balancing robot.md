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
  
  The basic working mechanism of the robot - 
  
  ![image](https://people.ece.cornell.edu/land/courses/ece4760/FinalProjects/f2018/amm452_fb262/amm452_fb262/amm452_fb262/images/overview_controlLoop.png)
  
  Components | Feasibility | Advantages | Disadvantages
  -----------| ----------- | ---------- | -------------
  Inertial Measurement Unit (IMU) | 
