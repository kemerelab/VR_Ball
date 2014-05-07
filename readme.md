#Instruction
##Prerequisites

* Two Logitech M90/M100 mice
* Ubuntu OS
* Blender:  
  `$ sudo apt-get install blender`  
* git (to get the code):  
  `$ sudo apt-get install git`  
* xinput:  
  `$ sudo apt-get install xinput`  
* python3.3 numpy & scipy:  
  `$ sudo apt-get install python3-numpy python3-scipy`

##Install and Run

1. Get the code:  
  `$ git clone https://github.com/kemerelab/BallTreadmill_VirtualSceneDisplay`  
2. Set up a group called **vr-users** and add yourself to that group.  
  `$ sudo addgroup vr-users`  
  `$ sudo adduser yourname vr-users`
3. Copy some **udev** rules to your system (**/etc/udev/rules.d/**): (**_$/_** will refer to the directory where you downloaded the code): **$/linux/etc/udev/rules.d/52-events.rules** will set up r/w permissions for when you connect an input device.
4. Copy **$/linux/usr/local/bin/findxinput-g500.py** into **/usr/local/bin/**. Make sure they are executable.  
  `$ sudo chmod +x findxinput-g500.py`  
  It is the script for soft detaching the optical mice when the program starts.
5. `$ ./standalone 1`  
  will print the readout from the first optical mouse to stdout. The _readout_ binary is for communicating with Blender through Unix sockets (Make sure they are executable).
6. Open the **$/figure 8 maze.blend**. Link all **$/python scripts/*.py** to it. 
7. Plug in the Arduino Pro chip. Upload **$/Arduino Pro/PyArduino** to the chip.
8. If everything went right, when you start the game mode (press 'P'), you can use optical mice to navigate the camera in virtual figure 8 maze and LED on Arduino will turn on. And the LED will be off for 2 seconds as soon as the camera enters 2 white areas in the maze alternatively.

##Q&A

* **Q:** The optical mice can control the camera, but the Arduino Pro LED doesn’t turn on anyway.  
  **A:** You might need to open another terminal, and open python3 to initialize serial transmission. (the same method as that in cameraview.py)  
