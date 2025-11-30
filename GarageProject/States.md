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
	```