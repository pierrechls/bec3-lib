# BeC3-lib

[![Version](https://img.shields.io/badge/version-1.0-green.svg)](https://img.shields.io/badge/version-1.0-green.svg) [![Build status](https://img.shields.io/badge/build-passing-green.svg)](https://img.shields.io/badge/build-passing-green.svg) [![Platform](https://img.shields.io/badge/platform-Linux%20%7C%20OS%20X%20%7C%20Windows-lightgrey.svg)](https://img.shields.io/badge/platform-Linux%20%7C%20OS%20X%20%7C%20Windows-lightgrey.svg)

Project realised in IMAC Engineering School.

## Set up BeC3-lib

1) Download zip file or clone the git repository

    git clone https://github.com/PierreChls/BeC3-lib.git

2) Move it to your third-party directory

3) In your third-party's CMakeLists.txt, add Bec3-lib subdirectory's

    add_subdirectory(Bec3-lib)

4) In your project's CMakeLists.txt, include Bec3-lib directory's and set Bec3-lib

    include_directories(third-party/Bec3-lib/include/)
    set(Bec3-lib)

## Prior installation



### Install Web-Lite API (created by Bec3)

- Download [Web-Lite](https://drive.google.com/file/d/0ByN00DGNcsTBSUZDbWktbXh2RHM/view?usp=sharing)
- Install [JAVA ORACLE JDK 8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
- Install [SBT](http://www.scala-sbt.org/download.html)
- Follow the instructions in the README file

#### Run WebLite API

Linux and Mac OSX :

	./weblite-api

Windows :

	./weblite-api.bat

### Install CMake

Linux :

    $ sudo apt-get install cmake

Mac OSX :

    $ brew install cmake


### Install CURL

Download [CURL](http://curl.haxx.se/download.html)

## How to use

### Create a session
#### 1. Make an instance of the Bec3 class
```cpp
Bec3 mySession;
```
#### 2. Initialize the session
There are two ways to init the session, you can pass a json initialization file as a constructor parameter, or pass your username and password as constructor parameters too.
* The file way
```cpp
Bec3 mySession = new Bec3("assets/conf/Bec3.json");
```
Notice that you can delay the file initialization with the `initFromFile()` method
```cpp
Bec3 mySession;
mySession.initFromFile("assets/conf/Bec3.json");
```
* The login way
```cpp
Bec3 mySession = new Bec3("username", "password");
```

### Create an object
For create a virtual object, you need to add an object to your session. You had to use the `addObject()` method
```cpp
mySession.addObject("id", "type");
```
#### Object id
The id of the object is simply its name, you can choose whatever you want.
#### Object types
There are four types of object :
* gauge : The gauge can be "filled" by others objects of the BeC3 platform.
* slider : The slide can take a value between 0 and 255.
* light : Like a real light, it can take two states, true or false.
* msg-receiver : This object can receive a text message.

#### Example
```cpp
mySession.addObject("myLight", "light");
```
## Use an object
### Get the state of an objects
If you want to get the state of an object, the Bec class has the method `getObjectState()` which takes the ID of the object and which returns a state object.
```cpp
mySession.getObjectState("id");
```
You can perform four actions on a state :
* retrieve the ID (in a string)
  ```cpp
  mySession.getObjectState("id").getId();
  ```
* retrieve the string value
  ```cpp
  mySession.getObjectState("id").getString();
  ```
* retrieve the int value
  ```cpp
	mySession.getObjectState("id").getInt();
  ```
* retrieve the boolean value
```cpp
	mySession.getObjectState("id").getBool();
```

### Update the state of your objects
Each object have a state, depending of its type.
You had to update the different states of the objects before you want use it.
The method `updateObjects()` is made for that.
```cpp
mySession.updateObjects();
```
### Thank you for using our library. Have fun with BeC3 and BeC3-lib !
