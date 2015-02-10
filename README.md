###Discovery Bot API

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

Asynchronous (non-blocking) control

    robot.forward()     # Move forward at 100% speed
    robot.forward(100)  # Move forward at 100% speed
    robot.left(40)      # Turn left at 40% speed
    robot.right(50)     # Turn right at 50%
    robot.backward(90)  # Move back at 90% speed
    robot.stop()        # Stop the robot
    robot.move(100, 40) # Move the left wheel at 100% and the right wheel at 40%
