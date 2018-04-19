# "Hello, World" Example

So. Here goes with the obligatory "Hello, World" program.

## Step 1: Installing Java and other tools

### First, we need to install Java, and other tools to begin programming.

{% tabs %}
{% tab title="Windows" %}
Download and run the installer from [http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

Make sure to select the **Windows x64** version.
{% endtab %}

{% tab title="Mac OS" %}
Download and run the installer from [http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).

Make sure to select the **Mac OS X x64 **version.
{% endtab %}

{% tab title="Linux" %}
Use `$ sudo apt-get install openjdk-8-jdk` in the terminal to install java
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
The WPI plugins, and the Roborio are not compatible with Java 9. All links are provided to Java 8.
{% endhint %}

### Second, we need our IDE \(Integrated Development Environment\). With our IDE, Eclipse, we will edit, compile and deploy our Java programs

{% tabs %}
{% tab title="Windows" %}
The Eclipse installer can be downloaded from: [https://www.eclipse.org/downloads/](https://www.eclipse.org/downloads/)

Once downloaded, run the executable file, and select **Eclipse IDE from Java Developers **Then simply click install, and Eclipse will be installed.
{% endtab %}

{% tab title="Mac OS" %}
The installer can be downloaded from: [https://www.eclipse.org/downloads/](https://www.eclipse.org/downloads/)

Run the installer, and select **Eclipse IDE for Java Developers**, and click install
{% endtab %}

{% tab title="Linux" %}
There is an eclipse package in the repositories. This package is outdated, so it is preferred to download the eclipse installer from [https://www.eclipse.org/downloads/](https://www.eclipse.org/downloads/)

If you choose the package, just execute the command: `$ sudo apt-get install eclipse`

{% hint style="warning" %}
All of the visuals presented in this book are taken from Eclipse Oxygen \(the latest version\), but Eclipse Neon \(the one in the repositories\) still works for robot development
{% endhint %}

If you choose the download, run the installer, and select **Eclipse IDE for Java Developers**
{% endtab %}
{% endtabs %}

{% hint style="info" %}
When you start up Eclipse, it will ask you for a workspace directory. The default option is perfectly fine, but you may choose any directory on you system.
{% endhint %}

#### Next, we need the plugins from WPI, that installs the tools to deploy to the roborio, as well as the WPI libraries.

From Eclipse, click the **Help** &gt; **Install New Software**. The window that opens up will ask for a site to work with. Use `http://first.wpi.edu/FRC/roborio/release/eclipse/` Then select **Robot Java Development**, under **WPILIB Robot Development**. Finally click install, and accept the licenses agreements.

{% hint style="info" %}
The WPI plugins only installs the base libraries. Other third party libraries need to be installed separately. There are instructions on how Team 1732 keeps track of and add libraries on the git tutorial

{% page-ref page="git-github.md" %}
{% endhint %}

## Step 2: Writing Code

{% hint style="success" %}
Udemy Hello World tutorial for desktop Java: [https://www.udemy.com/java-tutorial/learn/v4/t/lecture/131404?start=0](https://www.udemy.com/java-tutorial/learn/v4/t/lecture/131404?start=0)
{% endhint %}

To begin, we need to create a new project, and fill in the files to do stuff.

To create a project, go to **File** &gt; **New...** &gt; **Project...**. In the window that pops up, select **WPI Robot Java Development** &gt; **Robot Java Project**. To create the project, we will need a name for the project, and type. Team 1732 does command based programming, and this tutorial is written specifically for Command based programming.

For the name, I selected `HelloWorld`

Now there is a project listed in the Package Explorer:

![](.gitbook/assets/eclipsepackageexplorer%20%281%29.png)

Double click, or click the little arrow to open the project, and see the various subdirectories in the project. 

{% hint style="info" %}
I have package presentation set to Heirarchical. It is not nessecary to change, but I think it looks better this way. The down arrow at the top of the package explorer has a menu where you can change there settings.
{% endhint %}

The only file you will need to edit for now is the Robot.java file. To open it, double click on the file name.

And now, we can actually write some code. Add the following line right after line 37.

{% code-tabs %}
{% code-tabs-item title="Robot.java:38" %}
```java
System.out.println("Hello, World!");
```
{% endcode-tabs-item %}
{% endcode-tabs %}

To run the program, right click on the the project in the Package explorer, and select **Run As...** &gt; **WPILib Java Deploy**.

{% hint style="warning" %}
You may get an error about the java compiler, like compiler not found. To fix this, go to **Window **&gt; **Prefrences**. In the window, select **Java **&gt; **Installed JREs**. There, select the JDK, rather than the JRE.
{% endhint %}

You will get an error when it attempts to deploy to the robot, unless you are connected to the roborio.

## Connecting to the Roborio

There are several ways to plug into the roborio:

{% tabs %}
{% tab title="USB cable" %}
To connect via a USB-B to USB-A cable, plug the USB-B end into the square usb port on the roborio. Then plug the USB-A end into your computer.
{% endtab %}

{% tab title="Ethernet cable" %}
Plug the Ethernet cable into the Ethernet port 
{% endtab %}

{% tab title="Wifi" %}
This option requires more setup. First you need to configure the radio. This only needs to be preformed for new radios, or when an update comes out.

Instructions can be found at [https://wpilib.screenstepslive.com/s/4485/m/13503/l/144986-programming-your-radio-for-home-use](https://wpilib.screenstepslive.com/s/4485/m/13503/l/144986-programming-your-radio-for-home-use)

Once the radio is imaged, connect the Roborio to the radio's first ethernet port and ask electrical to power it. Then connect to the wifi the radio creates from your computer.
{% endtab %}
{% endtabs %}

Once you have completed one of the processes above, running the program as described above, and it should work without a problem. Although, nothing will happen, becuase there is no Driverstation attached.

{% page-ref page="driverstation.md" %}



