```text
# Safety Function Diagram

### Function Call: Safety
Safety check logic.

```mermaid
sequenceDiagram
    Door_Control->>Safety: Safety_Sensor
    
    alt Obstacle Detected
        Safety-->>Door_Control: FALSE
        Note left of Door_Control: Safety_Ok := FALSE
    else Path Clear
        Safety-->>Door_Control: TRUE
        Note left of Door_Control: Safety_Ok := TRUE
    end
	```