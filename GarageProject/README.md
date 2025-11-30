# Garage Project

## 1. State Diagrams

### Task 1: Door Control (Motor)
State machine for the door logic.

```mermaid
stateDiagram-v2
    [*] --> 0
    
    0 --> 10 : Button Open
    
    10 --> 20 : Sensor Open
    10 --> 0 : Safety_Ok = FALSE
    
    20 --> 30 : Button Close
    
    30 --> 0 : Sensor_Close
    30 --> 20 : Safety_Ok = FALSE

	stateDiagram-v2
    [*] --> Off
    
    Off --> On : Motor_Moving = TRUE
    
    On --> Off : Timer finishes (10s)
    On --> On : Motor_Moving = TRUE (Reset)

	sequenceDiagram
    Door_Control->>Variables: Motor_Moving = TRUE
    Variables->>Light_Control: Reads variable
    
    Note right of Light_Control: Turns Light ON
    
    Door_Control->>Variables: Motor_Moving = FALSE
    Variables->>Light_Control: Reads variable
    
    Note right of Light_Control: Waits 10s and turns OFF

	sequenceDiagram
    Door_Control->>Is_Safe: Safety_Sensor
    
    alt Obstacle Detected
        Is_Safe-->>Door_Control: FALSE
        Note left of Door_Control: Emergency Stop
    else Path Clear
        Is_Safe-->>Door_Control: TRUE
        Note left of Door_Control: Move Motor
    end