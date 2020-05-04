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
  Inertial Measurement Unit (IMU) | __MPU 6050__ (IMU) is readily available and no special prerequisite knowledge | Includes both accelerometer and gyroscope. Uses I2C communication. Connections can be made by simply referring to the data sheet | It is a bit noisy and drifts and not perfectly accurate | 
  Brushless Motors | Any beginnner can work with motors. Easily available | Less noisy as compared to other DC motors. They also with come with an in-built motor driver system | Cannot be used for heavy robot applications. Motor torque is generally less for larger deviation from equilibrium |
  Power Source | Easy fixation and cheap | 12V battery can easily power the motor with a nominal capacity. Long-lasting and rechargeable. | Added weight of the battery may harm the robot performance. |
  PIC32 Microcontroller | Not so easy to program. A skilled programmer required. | Cheap and readily available. Very easy to program if its use is clear. | Beginners cannot easily program. Even the datasheets are company specific. |
 
