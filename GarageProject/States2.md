```text
# State Diagram: Light Task

### Task 2: Light Control
Light logic with timer.

```mermaid
stateDiagram-v2
    [*] --> Off
    
    Off --> On : Motor_Moving = TRUE
    
    On --> Off : Timer finishes (10s)
    On --> On : Motor_Moving = TRUE (Reset)