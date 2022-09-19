---
template: blog-post
title:  "University - Extra-Curricular Awards"
date:   2018-11-19 19:00
slug: /extra-curricular-awards-activities
---

The Extra-Curricular Award is an award given for attending five different activities (some had been split into parts), for at least a total of 30 hours (10 hours having to be interdisciplinary, outside my course).

I had been awarded this within my first year, although found myself attending some of the same activities in my second year, preparing myself for third year units, which gave me a total of over 100 hours of logged award activities (not including the three activities I have ran, Futures Friday challenge for the Computing Society, and also the Hackathons that counted towards a maximum of 10 hours each).

## Intro to Android Programming
*Hours: 10hrs*

This was the first activity I had attended and introduced us to creating Android Apps in Android Studio, this would provide useful in second year since the tasks we did in this award activity, were lab tasks to help us produce the first assignment.

When it came to my second year assignment I could easily go back to the [MMUCheeseApp
](https://github.com/Sean12697/MMUCheeseApp){:target="_blank"} I produced and quickly remember how I created an app with a list view, then from there implement the features that would lead me to gain 100% for that particular assignment.

This "Cheese App" was one of two Android Apps we produced for the award, but the other was a calculator, pretty simple but did introduce us to different layout types, as well as being further practice for learning to create an app (which I have also put on my [GitHub](https://github.com/Sean12697/Calculator){:target="_blank"}).

### Links

<!-- - Eventbrite: [](){:target="_blank"} -->
- Github Project: [https://github.com/Sean12697/MMUCheeseApp](https://github.com/Sean12697/MMUCheeseApp){:target="_blank"}

## C++ Programming: Intro
*Hours: 9hrs (19hrs)*

Being quiet a low level language, in the first part of this activity we initially learned how C++ has header files and how the general language works, this as demonstrated by producing a command line application which used randomness to calculate PI (being on my [GitHub](https://github.com/Sean12697/CalculatePi/blob/master/CalculatePi/CalculatePi.cpp){:target="_blank"}).

From there the next two labs were dedicated to using C++ in a games aspect, due to the lecturer teaching this activity being a tutor for games, but also for how prevalent it is used within the gaming industry.

Luckily he did supply us with some base code to work on, which I cloned and pushed to [GitHub](https://github.com/Sean12697/SFML_Avatar_Intro){:target="_blank"} once I finished my modifications in the activities, although from this I have understood that I prefer higher level languages (not having to necessarily deal with memory pointers as well, which I learned in my Algorithms unit using C++).

### Links

<!-- - Eventbrite: [](){:target="_blank"} -->
- Github Project: [https://github.com/Sean12697/CalculatePi](https://github.com/Sean12697/CalculatePi){:target="_blank"}

## Building 3D Models
*Hours: 3hrs (22hrs)*

This activity simply introduced us to the complex program that is Maya, we were taught how to interact with the environment, morph shapes and render them with lighting, below is one of the renders I produced after only under three hours of using Maya for the first time.

![Wine Glass Render](https://i.imgur.com/ixn94RP.jpg)

<!-- ### Links -->

<!-- - Eventbrite: [](){:target="_blank"} -->
<!-- - Github Project: [](){:target="_blank"} -->

## Web Mapping: Intro
*Hours: 3hrs (25hrs)*

COMING SOON

### Links

<!-- - Eventbrite: [](){:target="_blank"} -->
- Github Project: [https://github.com/Sean12697/Web-Mapping-Heatmap](https://github.com/Sean12697/Web-Mapping-Heatmap){:target="_blank"}

## Internet of Things: Building Smart Environments
*Hours: 10hrs (35hrs)*

In this activity we focused on devices such as sensors that can be used for IoT, particularly being Phidget (brand) devices (servos, RFID, etc), with these we initially connected to them via the proprietary piece of software, then through Java with the use of a library (`phidget21.jar`).

From there we used our Java code to send our sensor values to a server, this being one we create through another Java project, it wasn't too complex due to the nature of the activities being aim towards those not studying a Computing related course, but was a functional RESTful API (posting values through the URI).

Once this was done, we set up a SQLite Database to store these values, simply using the below snippet to execute a insert statement into the DB:

```Java
String updateSQL = "insert into sensorUsage(SensorName, SensorValue, TimeInserted) " + "values('" + sensorNameStr + "','" + sensorValueStr + "', now());";
stmt.executeUpdate(updateSQL);
```

Once we learned about this, we then moved onto MQTT, this being a lightweight protocol for IoT communication implementing a publish/subscribe transportation technology, allowing it to have a lightweight footprint on both the code needed to be written, but also on bandwidth (since the a subscribed client will not be persistently checking for updates).

Luckily there is a library for this as well (`org.eclipse.paho.client.mqttv3-1.1.1.jar`), as well as many public brokers (MQTT Servers, essentially), which we could create topics to publish/subscribe to (which holds data in a text based format, which can be parsed to another data format such as JSON).

As I gave an example of a snippet of code you would write to insert data into a SQLite database, below is a snippet of the lines of could you could write to insert a sensor value with the aforementioned library:

```java
final MqttTopic rfidTopic = client.getTopic(TOPIC_RFID);
final String rfid = rfidTag + "%";
rfidTopic.publish(new MqttMessage(rfid.getBytes()));
```

Using this knowledge for roughly the last three hours we were given the task of creating something with the Phidget devices, as well as the various forms of communication we can use to transmit data and pieces of scarp material to build with (cardboard). 

My small team of two of my peers created a simple door opener, which would activate a servo when you scan a valid RFID card onto the sensor, the code for this can be found on my peers [GitHub](https://github.com/MichaelNaylor89/PhidgetDoorOpener/blob/master/RFIDMotor.java){:target="_blank"}.

### Links

<!-- - Eventbrite: [](){:target="_blank"} -->
- Github Project: [https://github.com/Sean12697/PhidgetDoorOpener](https://github.com/Sean12697/PhidgetDoorOpener){:target="_blank"}

## MATLAB® for Scientists & Engineers / Research
*Hours: 10hrs (45hrs)*

Being one of the more organised activities that was in two parts, each part having a break and a chapter for MatLab to go through each either side of the short breaks, this was ran by Dr Stephen Lynch, a lecturer at the University that has written multiple books on MatLab.

The first chapter was going through some basic syntax of MatLab and how to write in it, how it handles variables and different types of statements.

<!-- #### Chapter 2: A Tutorial Introduction to the Image Processing Toolbox

For this chapter we used the popular image of lena to 

#### Chapter 3: An Introduction to Data Analysis, Visualisation and Differential Equations -->

### Links

- Eventbrite: [](){:target="_blank"}
- Github Project: [https://github.com/Sean12697/MATLAB_Workshop_Intro](https://github.com/Sean12697/MATLAB_Workshop_Intro){:target="_blank"}

## Intro to Node-Red
*Hours: 5hrs (50hrs)*

Node-Red is a visual platform to code without having to type any code (although can if you want to), we were introduced to how we can modularly drag blocks for the likes of Twitter to gather data, then use other blocks like sentiment analysis to determine tweets sentiment (being if it is a negative or positive tweet).

This is roughly what we did in the first hour or two, then bleeding into the second and third hours we were demonstrated how to implement other API's we might want to use, but are not necessarily build into Node-RED by default.

We covered how we could do this by getting an OpenWeatherMap API key and using a user-made 'palette' (a series of related blocks), from there we we able to create a 'flow', blocks of code that connected and ended up with something similar to the flow below:

![Node-RED Weather Flow](https://i.imgur.com/IQfv1n2.jpg)

What this does is it gets the weather just for Manchester in the OpenWeatherMap block, from there we use a function block we create, writing a bit of code to get the value we want from the given JSON data that OpenWeatherMap, which determines if the weather will be clear, then finally we tweet that to Twitter (which we have to provide another set of API keys for).

From here we then used an MQTT module, covering similar topics we did for the IoT activity, although it was not a prerequisite to have attended that activity to attend this one, which is why we ended up covering MQTT twice, although this time from another approach (without too much code).

Similar tp the other activities once we wrapped up the lab sheets, we were then given time to play with Node-RED, seeing what other palettes we could use and what we could do with them.

<!-- ### Links -->

<!-- - Eventbrite: [](){:target="_blank"} -->
<!-- - Github Project: [](){:target="_blank"} -->

## Intro to Mainframe Programming
*Hours: 5hrs (55hrs)*

COMING SOON

### Links

- Eventbrite: [https://www.eventbrite.co.uk/e/intro-to-mainframe-programming-5-award-hours-tickets-46034879564](https://www.eventbrite.co.uk/e/intro-to-mainframe-programming-5-award-hours-tickets-46034879564){:target="_blank"}
- Github Project: [https://github.com/Sean12697/intro-to-mainframe-programming-cobol](https://github.com/Sean12697/intro-to-mainframe-programming-cobol){:target="_blank"}

## Intro to Node-RED
*Hours: 6hrs (61hrs)*

COMING SOON

### Links

- Eventbrite: https://www.eventbrite.co.uk/e/intro-to-node-red-programming-the-internet-of-things-5-award-hours-tickets-46035194506[](https://www.eventbrite.co.uk/e/intro-to-node-red-programming-the-internet-of-things-5-award-hours-tickets-46035194506){:target="_blank"}
<!-- - Github Project: [](){:target="_blank"} -->

## IoT: Building Smart Devices
*Hours: 10hrs (71hrs)*

COMING SOON

### Links

- Eventbrite (Part 1): [https://www.eventbrite.co.uk/e/internet-of-things-building-smart-devices-pt-1-of-2-5-award-hours-tickets-46037624775](https://www.eventbrite.co.uk/e/internet-of-things-building-smart-devices-pt-1-of-2-5-award-hours-tickets-46037624775){:target="_blank"}
- Eventbrite (Part 2): [https://www.eventbrite.co.uk/e/internet-of-things-building-smart-devices-pt-2-of-2-5-award-hours-tickets-46038282743](https://www.eventbrite.co.uk/e/internet-of-things-building-smart-devices-pt-2-of-2-5-award-hours-tickets-46038282743){:target="_blank"}
<!-- - Github Project: [](){:target="_blank"} -->

## 3D Printing Intro
*Hours: 3hrs (74hrs)*

COMING SOON

### Links

- Eventbrite: [https://www.eventbrite.co.uk/e/3d-printing-intro-run-2-take-a-laptop-3-award-hours-tickets-46038482340](https://www.eventbrite.co.uk/e/3d-printing-intro-run-2-take-a-laptop-3-award-hours-tickets-46038482340){:target="_blank"}
<!-- - Github Project: [](){:target="_blank"} -->

## Stereoscopic 3D Film
*Hours: 3hrs (77hrs)*

COMING SOON

<!-- ### Links -->

<!-- - Eventbrite: [](){:target="_blank"} -->
<!-- - Github Project: [](){:target="_blank"} -->

## Leadership & Teamwork Training - Army Style
*Hours: 10hrs (87hrs)*

COMING SOON

### Links

- Eventbrite (Part 1): [https://www.eventbrite.co.uk/e/leadership-teamwork-training-army-style-pt-1-of-2-5-award-hours-tickets-46041895549](https://www.eventbrite.co.uk/e/leadership-teamwork-training-army-style-pt-1-of-2-5-award-hours-tickets-46041895549){:target="_blank"}
- Eventbrite (Part 2): [https://www.eventbrite.co.uk/e/leadership-teamwork-training-army-style-pt-2-of-2-5-award-hours-moved-to-thurs-31-may-tickets-46041876492](https://www.eventbrite.co.uk/e/leadership-teamwork-training-army-style-pt-2-of-2-5-award-hours-moved-to-thurs-31-may-tickets-46041876492){:target="_blank"}
<!-- - Github Project: [](){:target="_blank"} -->

## MATLAB® for Scientists & Engineers / Research
*Hours: 5hrs (93hrs)*

COMING SOON
<!-- https://twitter.com/Sean12697/status/1003644392098365440 -->

### Links

- Eventbrite: [https://www.eventbrite.co.uk/e/matlab-for-scientists-engineers-research-pt-1-of-2-5-award-hours-tickets-46043138266](https://www.eventbrite.co.uk/e/matlab-for-scientists-engineers-research-pt-1-of-2-5-award-hours-tickets-46043138266){:target="_blank"}
<!-- - Github Project: [](){:target="_blank"} -->

## Python Programming
*Hours: 3hrs (96hrs)*

COMING SOON

### Links

- Eventbrite: [https://www.eventbrite.co.uk/e/python-programming-next-steps-3-award-hour-tickets-46043265647](https://www.eventbrite.co.uk/e/python-programming-next-steps-3-award-hour-tickets-46043265647){:target="_blank"}
- Github Project: [https://github.com/Sean12697/simple-python-games](https://github.com/Sean12697/simple-python-games){:target="_blank"}

## Python Matplotlib
*Hours: 3hrs (99hrs)*

COMING SOON

### Links

- Eventbrite: [https://www.eventbrite.co.uk/e/python-matplotlib-publication-quality-data-plotting-3-award-hours-tickets-46042963744](https://www.eventbrite.co.uk/e/python-matplotlib-publication-quality-data-plotting-3-award-hours-tickets-46042963744){:target="_blank"}
<!-- - Github Project: [](){:target="_blank"} -->

## Adventures in Chemiluminscence
*Hours: 5hrs (104hrs)*

COMING SOON

<!-- ### Links -->

<!-- - Eventbrite: [](){:target="_blank"} -->
<!-- - Github Project: [](){:target="_blank"} -->