#Reference for Accelerometer Mouse

This is going to be a reference document for my thoughts on this example .ino script using an Arduino Pro-like microcontroller and an accelerometer. While a gyroscope combined with this device will be better, the code in here is a good starting point.

##Libraries

This code uses:

- Wire I2C Library from Arduino
- Adafruit Sensor and Accelerometer Libraries
- A V-USB mouse Library

The Adafruit and V-USB Libraries may easily be replaced, but separate forks should be compiled for each test to ensure that the code can work across not only diferent types but also microcontrollers from different vendors.

##Structure

The code is structured as:

- Variables
- - Define Pins: SDA, SCL
- - Allocate variables for processed data.
- - Set Minimum Movement Threshold and Range Values with respect to sensor and expected input for mouse library.
- - Clamp maximum speed, maybe acceleration
- Init
- - Serial Initialization (9600 baud in this example)
- - Set range and get an initial read
- Loop
- - Read raw sensor values
- - Process the data
- - Call mouse function using processed values.
- - Delay (not recommended, need new method)

###Inside the Accelerometer Processing

- Check that the Reading exceeds minimum threshold.
- Move based on the distance of the movement in proportion to the maximum range.
- Do this for X and Y.

##Useful details

A Minimum Movement Threshold seems nececssary for an acceleration-only based approach, but should not be necessary for gyroscope. Replace this with a calibration step.

There must be a better way to control the "twitchiness" of the output other than delaying the entire microcontroller.
