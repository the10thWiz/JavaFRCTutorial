# Motors

Now we get the fun part: actually making the robot do stuff. In this tutorial, we will identify a motor from the Roborio, and tell it to run.

### Theory

If you run current through a motor, the motor spins. AC motors accept AC power, and DC motors accept DC power. If you reverse the current, the motor spins backwards. The motor itself cannot do anything more.

But, we can still provide detailed controls to our motors, becuase there is a motor controller between the power source and the actual motor. There are several common motor controllers, each of which has unique capabilities.

* TalonSRX: the talon is the most common motor we use. It is also the most advanced on this list being capable of motion profiling, current limiting, and various other methods of control. Controlling the talon does require third party libriaries, specifically from [http://www.ctr-electronics.com/control-system/motor-control/talon-srx.html\#product\_tabs\_technical\_resources](http://www.ctr-electronics.com/control-system/motor-control/talon-srx.html#product_tabs_technical_resources)
* VictorSPX: the victor is similar to the talon, but missing some of the most advanced features. Victors can however follow talons, and are cheaper, so we use several of them in our robots. Victors are also dependent on the same libriary as the talons.
* Spark: the spark motor controller comes in the kit of parts, so many teams use them. We have only used them on practice bots, so knowing how to use the spark is mostly unnessecary. Sparks are also just able to control the speed of a motor, so they are the least useful on the list here.

From the previous tutorial, you learned how to create an instance variable, and write a method. Here, we will need to create another instance variable, and instatiate an object.

### Libriaries

The libriaries provide their functionality through the use of classes. To use the classes for the motor controllers, we will need to create an object that can control the motor. The libriaries to control the talon and the victor are very similar, with specific words swiched, while the spark is completely seperate.

A class can have static variables and methods, which are tied to the class, but a class can also have instance variables and methods, which are called on instances of the class. There is a special in most classes called a constructor, that creates an instance of the class, also called an object.

### Using the TalonSRX

First, we need an instance variable in the class, of the type `TalonSRX`. For example:

{% code-tabs %}
{% code-tabs-item title="SpinMotor.java:14" %}
```java
private TalonSRX motor;
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Now we have an instance variable. Next, we need to initialize the motor to a value in the `init()` method. To do this, we will use the following syntax:

{% code-tabs %}
{% code-tabs-item title="SpinMotor.java:18" %}
```java
motor = new TalonSRX(0);
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Now, lets break apart that statment. We are saying we want a `new TalonSRX` object, to be stored in `motor`. The 0 in between the parenthasees a parameter of the constructor. You can create more than one instance of a class, each of which can have diffrent values for its internal variables. The talon object created refers to a talon motor controller connected to the CAN network as device 0.

### Configuring the CAN network device IDs

{% hint style="danger" %}
Editing CAN IDs, and attaching motors is somewhat difficult. It also directly involves the electircal system, so you can and should ask for help from electrical when configuring the CAN network
{% endhint %}

To configure the device IDs of the talons, simply go to [http://roborio-1732-frc.local/](http://roborio-1732-frc.local/), and the following webpage opens up:

To edit a talon's configuration, simple open it up, and you can edit its name and its device ID. There is also an option to make the lights flash, which allows you to identify which talon is which.

### Motor Control

In the last tutorial, we created a method that set the subsystem's speed variable. Now, whenever we call this method, we will want to tell the motor to spin at said speed. To do this, we use one of the TalonSRX's methods, namely `.set(ControlMode mode, double speed);`

There are several control modes avalible on the talons and victors:

* `ControlMode.PercentOutput`: Percent output accepts a percentage \(expressed as a decimal, e.g. 0.50 = 50%\). To run the motor in reverse, you can use negative numbers.
* `ControlMode.Current`: Current control allows us to control the amount of current passing through the motor. This value is double measured in amps.
* `ControlMode.Disabled`: Sets the motor to have no current. Similar to Percent or Current, if the value is 0.
* `ControlMode.Follower`: Sets this motor to follow another. Basically, the motor copies what ever the other one does, so you only have to set the master. The parameter is the device ID of the motor to follow.

{% hint style="info" %}
There are also Position, Velocity, MotionMagic, MotionProfile, and MotionProfileArc modes. These are advanced features, and will be covered in the section of autonoumous driving.
{% endhint %}

To begin, we will use percent output, as it is the simplest method to understand. We will call the set method on motor, whenever we set the speed variable. Try to implement this on your own, but the code needed is provided below.

In `setSpeed`

{% code-tabs %}
{% code-tabs-item title="spinMotor.java:23" %}
```java
motor.set(ControlMode.PercentOutput, speed);
```
{% endcode-tabs-item %}
{% endcode-tabs %}

And in `stop`

{% code-tabs %}
{% code-tabs-item title="spinMotor.java:36" %}
```java
motor.set(ControlMode.PercentOutput, 0);
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Once you have the lines added, the robot will run the motor in slot 0 while Teleop is enabled.

{% hint style="success" %}
Try changing the port the motor is connected to. Remeber to also edit the CAN config. Solution to be posted later.
{% endhint %}

{% hint style="success" %}
Try setting the motor to a different speed. Solution to be posted later.
{% endhint %}



