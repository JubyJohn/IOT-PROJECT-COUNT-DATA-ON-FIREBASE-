# IOT PROJECT: COUNT DATA ON FIREBASE


## AIM

To create a Firebase project with a realtime database and to store the count of push button in the database using the ESP8266 interfaced with push button.

## COMPONENTS

1.	ESP8266 NodeMCU
2.	Push button Module
3.	Jumper Wire
4.	USB cable 


## CONNECTION

### Push Button Module Pin Diagram


 ![push-button-module](https://github.com/user-attachments/assets/b1630b48-fe38-425f-a42f-8ee64c74ed5c)

<br> GND = ground   ---->  GND
<br> +   = power supply  ---->  3V3
<br> S   = Output     ---->  D2


## PROCEDURE

<br> Step 1 :  Create a Firebase Project
<br> Step 2 :  Interface ESP8266 microcontroller to Visual Studio Code using port.
<br> Step 3 : Interface ESP8266 microcontroller with push button and print the digital values on serial monitor.
<br> Step 4 : Install the Firebase-ESP-Client Library.Then, program the ESP8266 to Interface with Firebase
<br> Step 5 : Need to insert your network credentials, URL database, and project API key for the project to work.

### Step 2 :  Interface ESP8266 microcontroller to Visual Studio Code using port

<br> Visual Studio Code combines the simplicity of a code editor with what developers need for their core edit-build-debug cycle. It provides comprehensive code editing, navigation, and understanding support along with lightweight debugging, a rich extensibility model, and lightweight integration with existing tools.

#### 1.Visual Studio Code Installation

<br> -> Go to Google, type VS Code and download from its official site according to your OS.
<br> -> Open the downloaded file and start Setup, Install and finish
<br> -> Open VS code, on left bar click on Extensions and search for platformio, then install it. After completing installation, close and open again VS code.
<br> Visual Studio Code Installed

#### 2.Create a New Project

<br> -> Open VS code, on left bar click on platform.io then click on open and on right side
        &nbsp; - Project Name
        <br>  - Board: NodeMCU 1.0( ESP - 12E  Module)
        <br>  - Finish
<br> -> On platformio.ini , enter the library file on lib_deps
<br> -> On left bar, click on src and open main.cpp. Here you can enter the program.

 ![VS Code](https://github.com/user-attachments/assets/a87be81d-11bf-41d3-98eb-79828b494a36)


## OUTPUT


![IMG_1](https://github.com/user-attachments/assets/e2823589-d0b4-405f-93f7-15e7188c04ac)

![IMG_2](https://github.com/user-attachments/assets/dcf55626-6a13-4f6b-b21a-ab19e5d12097)

![IMG_3](https://github.com/user-attachments/assets/636a6bdb-66e5-41b5-858c-a55dd293fcca)

## REFERENCE

<br> Visual Studio Code Installation: https://code.visualstudio.com/download
