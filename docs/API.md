---
title: API
---

The following is the API for the stepper motor subsystem. This includes messages that the subsystem must receive and interpret, but will never send, namely message type 2 and 3 (used to determine target motor position). Each message type will be utilized by the stepper motor subsystem, as message types 1-3 provide necessary information for proper device function.

|Message Type <br> byte 1-2 <br>(uint16_t) | Description | Sending or Recieving? |
|-------------------|---------------|-------------|
|0                  | Status Code   | Sending Globally |
|1                  | Drive Mode    | Receiving |
|2                  | Sensor Data   | Receiving |
|3                  | Path Selection| Receiving |

## Message Type 0: Status Code
|         |  Byte 1-2  | Byte 3 | 
|---------|----------|---------|
|Var Name | msg_type | status  |
|Var Type | uint16_t | uint8_t |
|Min Val  | 0        | 0       | 
|Max Val  | 3        | 3       |
|Example  | 0        | 2       |

**Key to status code messages:** 

| Byte 3 (uint8_t) | Description |
|------------------|-------------|
| 0x00             | Offline     |
| 0x01             | Online      |
| 0x02             | Waiting     |
| 0x03             | Error       |

>Note: Team 201 is currently assembling and testing their respective subsystems, and is in the process of identifying, cataloging, and typifying device error states. As such, this page will be updated in time to reflect valid error states.

## Message Type 1: Drive Mode 

|         |  Byte 1-2  |  Byte 3 |
|---------|-----------|----------|
|Var Name | msg_type  | color    |
|Var Type | uint16_t  | uint8_t  | 
|Min Val  | 0         | 0        |
|Max Val  | 3         | 2        |
|Example  | 2         | 1        |

**Key to drive mode messages**  

| Byte 3 (uint8_t) | Description |
|------------------|-------------|
| 0x00             | Automatic   |
| 0x01             | Direct Drive|

## Message Type 2: Sensor RGB Data 

|         |  Byte 1-2  |  Byte 3 |
|---------|-----------|----------|
|Var Name | msg_type  | color    |
|Var Type | uint16_t  | uint8_t  | 
|Min Val  | 0         | 0        |
|Max Val  | 3         | 2        |
|Example  | 2         | 1        |

**Key to sensor data messages**

| Byte 3 (uint8_t) | Description |
|------------------|-------------|
| 0x00             | Orange         |
| 0x01             | Blue       |
| 0x02             | Pink        |

## Message Type 3 : Path Selection  

|         |  Byte 1-2  | Byte 3 |
|---------|------------|--------|
|Var Name | msg_type   | path   |
|Var Type | uint16_t   | uint8_t|
|Min Val  | 0          | 0      |
|Max Val  | 3          | 2      |
|Example  | 2          | 2      |

**Key to path selection messages:**

| Byte 3 (uint8_t) | Description |
|------------------|-------------|
| 0x00             | left        |
| 0x01             | center      |
| 0x02             | right       |