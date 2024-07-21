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
        <br>  - Project Name
        <br>  - Board: NodeMCU 1.0( ESP - 12E  Module)
        <br>  - Finish

  ![VS Code](https://github.com/user-attachments/assets/a87be81d-11bf-41d3-98eb-79828b494a36) 
        
<br> -> On platformio.ini , enter the library file on lib_deps
<br> -> On left bar, click on src and open main.cpp. Here you can enter the program.


## CODE

### CODE WITHOUT USING INBUILD FUNCTION

'''#if defined(ESP32)
    #include <WiFi.h>
    #elif defined(ESP8266)
    #include <ESP8266WiFi.h>
    #endif
    #include <Firebase_ESP_Client.h>
    #include <addons/TokenHelper.h>
    #include <addons/RTDBHelper.h>
     #define WIFI_SSID "-----------------"
    #define WIFI_PASSWORD "------------------"
    #define API_KEY "--------------------------------------------"
    #define DATABASE_URL "---------------------------------------"
    #define USER_EMAIL "-----------------"
    #define USER_PASSWORD "---------"
    FirebaseData fbdo;
    FirebaseAuth auth;
    FirebaseConfig config;
    int count = 0 ;
    String msg; 
    void Connect_WiFi();
    void Firebase_Store(String PATH,String MSG);
    String Firebase_getString(String PATH);
    int key();
    void uploadVal(int);
    void setup()
    {
         Connect_WiFi(); 
         pinMode(D2,INPUT);
    }
    void loop()
    {
      int k;
      k=key();
      if(k==1)
      {
        count ++;
        Serial.println(count);
        uploadVal(count);
      }
    }
    void Connect_WiFi()
    {
          Serial.begin(9600);
          delay(100); 
          WiFi.disconnect();
          delay(800); 
          Serial.println("Connecting to Wi-Fi"); 
          WiFi.begin(WIFI_SSID, WIFI_PASSWORD);
          Serial.print("Connecting to Wi-Fi");
          delay(100);
          while (WiFi.status() != WL_CONNECTED)
          {
            Serial.print(".");
            delay(300);
          }
          Serial.println();
          Serial.print("Connected with IP: ");
          Serial.println(WiFi.localIP());
          Serial.println();
          Serial.printf("Firebase Client v%s\n\n", FIREBASE_CLIENT_VERSION);
          config.api_key = API_KEY;
          auth.user.email = USER_EMAIL;
          auth.user.password = USER_PASSWORD;
          config.database_url = DATABASE_URL;
          config.token_status_callback = tokenStatusCallback;
           #if defined(ESP8266)
            fbdo.setBSSLBufferSize(2048 /* Rx buffer size in bytes from 512 - 16384 */, 2048 /* Tx buffer size in bytes from 512 - 16384 */);
          #endif
          Firebase.begin(&config, &auth);
          Firebase.reconnectWiFi(true);
          Firebase.setDoubleDigits(5);
          config.timeout.serverResponse = 10 * 1000;
    }
    void Firebase_Store(String PATH,String MSG)
    {
          Serial.print("Uploading data \" ");
          Serial.print(MSG);
          Serial.print(" \"  to the location \" ");
          Serial.print(PATH);
          Serial.println(" \"");
          Firebase.RTDB.setString(&fbdo, PATH, MSG);
          delay(50);
    }
    String Firebase_getString(String PATH)
    {
      String msg = (Firebase.RTDB.getString(&fbdo, PATH) ? fbdo.to<const char *>() : fbdo.errorReason().c_str());
      delay(50);
      return msg;
    }
    int key()
    {
      int x=0;
      while(digitalRead(D2)==0)
      {
        x=1;
        delay(50);
      }
      return x;
    }
    void uploadVal(int n)
    {
        int r,a[10],i=0;
        while(n>0)
        {
          r=n%10;
          n=n/10;
          a[i]=r;
          i++;
        }
        msg ="";
        for(i--;i>=0;i--)
        {
            if(a[i]==0)
            {
              msg += "0";
            }
            else if(a[i]==1)
            {
              msg += "1";// msg =msg+ "1"
            }
            else if(a[i]==2)
            {
              msg += "2";
            }
            else if(a[i]==3)
            {
              msg += "3";
            }
            else if(a[i]==4)
            {
              msg += "4";
            }
            else if(a[i]==5)
            {
              msg += "5";
            }
            else if(a[i]==6)
            {
              msg += "6";
            }
            else if(a[i]==7)
            {
              msg += "7";
            }
            else if(a[i]==8)
            {
              msg += "8";
            }
            else if(a[i]==9)
            {
              msg += "9";
            }
        }
        Serial.println(msg);
        Firebase_Store("/test/count",msg);
    }'''

## OUTPUT


![IMG_1](https://github.com/user-attachments/assets/e2823589-d0b4-405f-93f7-15e7188c04ac)

![IMG_2](https://github.com/user-attachments/assets/dcf55626-6a13-4f6b-b21a-ab19e5d12097)

![IMG_3](https://github.com/user-attachments/assets/636a6bdb-66e5-41b5-858c-a55dd293fcca)

## REFERENCE

<br> Visual Studio Code Installation: https://code.visualstudio.com/download
