---
title: API
---

The following is the API for the stepper motor subsystem. This includes messages that the subsystem must receive and interpret, but will never send, namely message type 2 and 3 (used to determine target motor position). Each message type will be utilized by the stepper motor subsystem, as message types 1-3 provide necessary information for proper device function.

A link to an MPLAB X project demonstrating effective message transfer will soon be available *here*.

|Message Type <br> byte 1 <br>(uint8_t) | Description | Sending or Recieving? |
|-------------------|---------------|-------------|
|0                  | Status Code   | Sending Globally |
|1                  | Drive Mode    | Receiving |
|2                  | Sensor Data   | Receiving |
|3                  | Path Selection| Receiving |

## Message Type 0: Status Code
|         |  Byte 1  | Byte 2 | 
|---------|----------|---------|
|Var Name | msg_type | status  |
|Var Type | uint8_t | uint8_t |
|Min Val  | 0        | 0       | 
|Max Val  | 3        | 3       |
|Example  | 0        | 2       |

**Key to status code messages:** 

| Byte 2 (uint8_t) | Description |
|------------------|-------------|
| 0x0             | Waiting     |
| 0x1             | Online      |



## Message Type 1: Drive Mode 

|         |  Byte 1  |  Byte 2 |
|---------|-----------|----------|
|Var Name | msg_type  | color    |
|Var Type | uint8_t  | uint8_t  | 
|Min Val  | 0         | 0        |
|Max Val  | 3         | 2        |
|Example  | 2         | 1        |

**Key to drive mode messages**  

| Byte 2 (uint8_t) | Description |
|------------------|-------------|
| 0x0             | Automatic   |
| 0x1             | Direct Drive|

## Message Type 2: Sensor RGB Data 

|         |  Byte 1  |  Byte 2 |
|---------|-----------|----------|
|Var Name | msg_type  | color    |
|Var Type | uint16_t  | uint8_t  | 
|Min Val  | 0         | 0        |
|Max Val  | 3         | 2        |
|Example  | 2         | 1        |

**Key to sensor data messages**

| Byte 2 (uint8_t) | Description |
|------------------|-------------|
| 0x0             | Orange         |
| 0x1             | Blue       |
| 0x2             | Pink        |

## Message Type 3 : Path Selection  

|         |  Byte 1  | Byte 2 |
|---------|------------|--------|
|Var Name | msg_type   | path   |
|Var Type | uint8_t   | uint8_t|
|Min Val  | 0          | 0      |
|Max Val  | 3          | 2      |
|Example  | 2          | 2      |

**Key to path selection messages:**

| Byte 2 (uint8_t) | Description |
|------------------|-------------|
| 0x0             | left        |
| 0x1             | center      |
| 0x2             | right       |