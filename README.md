#Discovery Bot API

## The Discovery Bot

The discovery bot is a fun and simple raspberry pi robot for all ages. This project allows you to easily control your robot through a python API. This project is required for the discovery blockly project. 

The API is dived into simple classes and modules used to control different aspects of the discovery bot.

## Download Disovery Bot Image
Get the latest image for the discovery bot for your raspberry pi

*http://images.discoverykit.org/DiscoveryBot/stable/*

## Using the API in your python project

Import the whole discovery API into your project
    import discovery_bot

You can also import only the modules that you need (e.g. movement)
    from discovery_bot import Movement

## Movement

Create an instance of the movement class

    import discovery_bot
    robot = discovery_bot.Movement()

Asynchronous (non-blocking) control

    robot.forward()     # Move forward at 100% speed
    robot.forward(100)  # Move forward at 100% speed
    robot.left(40)      # Turn left at 40% speed
    robot.right(50)     # Turn right at 50%
    robot.backward(90)  # Move back at 90% speed
    robot.stop()        # Stop the robot
    robot.move(100, 40) # Move the left wheel at 100% and the right wheel at 40%
    robot.move(-50, 10) # Move the left wheel backwards at 50% speed and the right wheel at 10% speed

Synchronous (blocking) control

    robot.forward(90, 5)    # Move forward for 5 seconds
    robot.left(50, 1.5)     # Turn left for 1.5 seconds
    robot.move(100, 10, 5)  # Move left motor at 100% and the right wheel at 10% for 5 seconds

## Ultrasound
The ultrsound provides functions to read the distance of objects to the front of the robot. You can get a relative value from 0-100 or a rough value in centimeters.

    from discovery_bot import Ultrasound
    usound = Ultrasound()
    usound.read()    # Get a normalized value between 0-100
    usound.distance  # Returns a rough distance in CM

## Camera
The camera class projects a means to set the angle on the camera mount as well as some basic functions for controlling the discovery bots camera.

    from discovery_bot import Camera
    camera = Camera()
    camera.angle(90)    # Set the angle of the camera servo, between 0 - 120
    camera.capture()    # Capture a picture with the camera and save to filesystem
    
## Servo
This is the base class for all servos connected to the discovery bot. Using this class you can controll any servo connected to one of the four servo ports on the discovery bot.

    import discovery_bot
    from discovery_bot import Servo
    servo0 = Servo(discovery_bot.pins.SERVO_0)
    left = Servo(discovery_bot.pins.SERVO_LEFT_MOTOR)
    servo0.set_normalized_speed(100)  # Treat servo as continous and provide a speed value
    servo0.set_normalized_angle(90)   # Standard servo and provide angle 0 - 120
    servo0.set_normalized(1200)       # Provide a pulse width to servo
    
## Line Sensor

    import discovery_bot
    sensor = discovery_bot.LineSensor(discovery_bot.pins.LINE_SENSOR)
    sensor.on_line()    # Return true if line detected
    sensor.off_line()   # Return true if no line detected
    sensor.last_state() # Remember the last known state of the sensor
    
## IO
Base class for all GPIO based operations

    import dicovery_bot
    from discovery_bot import IO
    gpio = IO(discovery_bot.pins.BUZZER)
    gpio.on()
    gpio.on_for(1) # Turn on for 1 second
    gpio.off()
    gpio.is_high()
    gpio.is_low()
    
