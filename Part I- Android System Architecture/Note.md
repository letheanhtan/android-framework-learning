# Android System Architecture
https://blog.csdn.net/huaxun66/article/details/78135556

* Essence of Android is to
    
    * Add Java virtual machine Dalvik/ART to standard Linux System
    * Build a Java application framework on Dalvik/ART virtual machine
    * All applications based on Java applicaition framework
* Android is divided into four layers
    
    * Application Layer
    * Application framework layer
    * System runtime layer
    * Linux Kernel layer

![Android System Archiecture](/images/android_system_architecture.png  "Android System Architecture")

## Application layer

* Provide some core packages: email, SMS, calendar, maps, browsers and contact management

* At the same time, developers can also use Java language to design and write their own applications

## Application framework layer

* Provide developers APIs they need to develop applications

* We usually use this layer call to develop our applications, and of course the system applications

* This layer written in Java code, so can also called Java framework

* The application framework layer included ten parts:

    * Activity Manager

        * Control all aspects of application life cycle and activity stack
    * Location Manager

        * Provide access to the location service, allowing an applicatin to receive update about location changes
    * Package Manager
        * System by which application are able to find out information about other application currently installed on the device
    * Notification Manager
        * Allow application to display alert and notification to user
    * Resource Manager
        * Provide access to non-code embedded resources such as strings, color settings and user interface layouts
    * Telephony Manager
        * Provide information to the application about the telephony service available on device such as status and subscriber information
    * Window Manager
    * Content Providers
        * Allow application to publish and share data with other application
    * View System
        * Extensible set of views used to create application user interfaces
    * XMPP service

## System Runtime layer
* Divided into two parts:
    
    * C/C++ Library
    * Android Runtime library

* C/C++ Library

    * Can be used by different components in the Android System and serve developer through the application framework. 
    * Consist of nine subsystems: 
        
        * Surface Manager
        * Media framework
        * SQLite
        * OpenGL  ES
        * FreeType
        * Webkit
        * SGL
        * SSL
        * libc

* The Android Runtime library
    
    * Divided into two parts:
    
        * Core Libraries
             
        * ART ( Android Runtime) (After Android 5.0, Dalvik Virtual Machine is replaced by ART)
    * Core Libraries
        * Provide most functionality of Java core language library, so developer can write Android application using Java language

    * Dalvik virtual machine
    
        * Compare to JVM, Dalvik virtual machine is specific for mobile devices
        * Allow multiple instances of virtual machine to run simutanously in the limited memory
        * Each Dalvik application executed as a separate Linux process
        * The separate process prevent all program from being closed when the virtual machine crashes.
        * Each time the application run, the bytecode need to be converted to machine code by just-in-time compiler, which slow down the application's running efficiency.

    * ART

        * Use Ahead-Of-Time approach (AOT), the dex file is convert once the application installed. 

        * The performance is better

## The Android Hardware abstraction layer
* User space code can not directly access Android Linux kernel device driver
* Therefore, app and system services use HAL to interact with kernel driver
* OEMs implement HAL driver modules for their prorietary hardware


## The Linux kernel layer

* Android Core system service based on the Linux kernel, some specific driver have been added

* Abstraction layer for hardware and software stack
* Kernel is core of any OS
* Linux Kernel sit in the bottom of Android Architecture
* Provide support for many features
    
    *   Memory management
    *   Security management
    *   Process management
    *   Device management

* Contains all the drivers that help Android device to communicate with other hardware devices.

# Android System Source Code
Reference link

* https://www.androiddevtools.cn/
* http://androidxref.com/

## Whole Frame
The root directory structure of android 7.0 is shown as following:

![Code structure whole frame](/images/code_structure_whole_frame.png  "Code structure whole frame")


## Application layer

![Code structure application layer](/images/code_structure_application_layer.png  "Code structure application layer")


## Application framework layer

* The core part of the system

* On the one hand, it provides an interface to application layer. 

* On the other hand, it connects to C/C++ library and HAL (Hardware abstraction layer)

* The frameworks/base directory structure is as follow:

![Code structure frameworks/base](/images/code_structure_frameworks_base.png  "Code structure frameworks/base")
