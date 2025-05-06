---
title: API
---

The following is the API for the stepper motor subsystem. This includes messages that the subsystem must receive and interpret, but will never send, namely message type 2 and 3 (used to determine target motor position). Each message type will be utilized by the stepper motor subsystem, as message types 1-3 provide necessary information for proper device function.

A link to an MPLAB X project demonstrating effective message transfer is available [here](static/media/Final_Project.X.zip).


*The following table can also be found on Team 201's communication diagram page.

## **Team Message Structure**
UART messages are sent from team member to team member in an 8-byte format. Each byte has a specifix role, outlined in Table 1 below. 

*Table 1: Message Byte Structure*

|**Byte Number**|0-1|2|3|4|5|6-7|
|---|---|---|---|---|---|---|
|**Byte Contents**|AZ|Sender ID|Receiver ID|Message Type|Message Data|YB|

The message prefix AZ and suffix YB function as a message start/stop indicator, allowing team members to efficiently filter out extraneous noise on UART lines as well as anticipate a prescribed message format. Sender and Reciever IDs (see table 2) are used to identify to which team member a message is intended, as well as provide a marker of who sent the message. This is advantageous given the daisy-chain layout of Team 201's project, as messages will be sent from member to member until they are terminated by their recipient or their sender, depending on message type (see Table 3 for Message Type IDs and their respective data).

*Table 2: Team IDs*

| Team member (Role) | Team ID |
|---|---|
|JC <br>(HMI)| H |
|Eric <br>(Sensor)|S|
|Marcus <br>(MQTT Server)|M|
|Bradley <br>(Actuator)|A|
|Broadcast <br>(sends to all members)|X|

*Table 3: Message Types and Data Structure*

| Message Type (UINT8_t) | Message Data info (UINT8_t) |
|---|---|
|**Type 0: Initialization** <br>**Message Type ID:** 0x00|**Message Contents:**<br>0x00 *Enable all systems*|
|**Type 1: Drive Mode** <br>**Message Type ID:** 0x01|**Message Contents:**<br>0x00 *Autonomous Function*<br>0x01 *User-Controlled Function*|
|**Type 2: Sensor Data** <br>**Message Type ID:** 0x02|**Message Contents:**<br>0x00 *Sensor detects Orange*<br>0x01 *Sensor detects Blue*<br>0x02 *Sensor detects Pink*|
|**Type 3: Path Selection** <br>**Message Type ID:** 0x03|**Message Contents:**<br>0x00 *Orient motor Left*<br>0x01 *Orient motor Right*<br>0x02 *Orient motor Right*|