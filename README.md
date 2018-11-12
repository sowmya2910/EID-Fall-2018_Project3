# EID-Fall-2018-Project_3 - Client-AWS IoT-Server
# DHT22 Temperature/Humidity Sensor, QT5, Python3.x, Raspberry Pi 3, AWS, MQTT, Node.js, Boto3

## PROJECT WORK

This project is a combined effort of the following people:
### Sowmya Ramakrishnan - Server, Client side UI, Database, QT Script, calculations, AWS Lambda, SQS, MQTT, Extra Credits
### Vinayak Srivatsan Kovalam Mohan - Server-side script, Plot functions, calculations, AWS IoT Setup, Extra Credits

## PROJECT DESCRIPTION

This project uses two Raspberry Pis - one is the sensor while other is the client, both running QT UIs.
The sensor takes runs an interactive QT UI Interface that takes temperature/humidity values/readings using the read() function from a connected sensor (using the ADAFruit Library and GPIO Pin 4) at an interval of 5 seconds, sends the temperature and humidity values to AWS IoT Thing (EIDProject3) using MQTT in json format every 5 seconds, and displays in the QT 8 values - Maximum, Minimum, Current and Average Temperature and Humidity. Timestamp is also displayed. It also has a button that allows for change of unit from celcius (defaultly obtained) to fahrenheit.
All of this data from sensor is stored in a .csv (comma-separated value) file.
The sensor then runs an interactive QT UI that allows the remote client to request and display data as well as plot graphs. (Client)
In the middle, the data in AWS IoT is handled by a Lambda Function that uses Node JS to calculate various parameters and put all data in an AWS SQS Queue as 8-value messages.
The Client, requesting data, gets it from the AWS Queue (10 or less at a time, upto 30) using Boto3 resource. It also indicates communication failures/data not present error. The Client has a button to change between temperature units (C and F).
The Client and Server sides are implemented in QT.
AWS is the middleman between the client and the server.

Thus, all minimum requirements have been met. 

## PROJECT ADDITIONS (EXTRA CREDIT)

- A Login Screen on the Server as well as the Client side to secure the application.
- 
- A Clear button that clears all data displayed and a Close button that closes Window
- Separate buttons for plots of temperature and humidity
- A Sensor State button on the QT GUI which tells if the sensor is connected/disconnected

## INSTALLATION/RUNNING INSTRUCTIONS

- Install tornado using the command : pip install tornado
- Install matplotlib using the command : sudo apt-get install python3 matplotlib'
- Change IP of the server as appropriate
- Clone this repository
### Server
- Run project2.py to open up the QT GUI and get and display data on the server side
- Run server.py to launch websocket server
### Client
- Open login.html, give username = username and password = psw to enable successful login
- The user is automatically re-directed to the HTML UI Webpage where values are displayed

## REFERENCES

https://www.w3schools.com/howto/howto_css_login_form.asp
https://www.geeksforgeeks.org/working-csv-files-python/
http://blog.glehmann.net/2014/12/23/Raspberry-Pi-as-a-temperature-logger/
https://stackoverflow.com/questions/24123715/degree-fahrenheit-celsius-symbols-ascii-nsstring
https://robots.thoughtbot.com/json-event-based-convention-websockets
https://os.mbed.com/cookbook/Websockets-Server#code
https://stackoverflow.com/questions/12839567/converting-string-to-number-in-javascript-jquery
https://www.w3schools.com/jsref/jsref_isnan_number.asp
https://www.w3schools.com/html/default.asp
https://www.w3schools.com/css/default.asp
https://www.w3schools.com/jquery/default.asp
https://www.w3schools.com/js/default.asp
https://github.com/adafruit/Adafruit_Python_DHT
