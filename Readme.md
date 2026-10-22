# Black Box Testing

For this lab I chose instagram, specifically its Login feature

## Equivalence Partitioning

### Valid Partitions
    - Existing username + correct password
        - Value: testuser / Correctpass123
        - Expected: Login successfull

### Invalid Partitions
    - Existing username + incorrect password
        - Value: testuser / WrongPass
        - Expected: Error message

    - Nonexistant username
        - Value: fakeusername123 / Passoword123
        - Expected: Validation error

    - Empty username
        - Value: "" / Password123
        - Expected: Validation error
    
    - Empty password
        - Value: testuser / ""
        - Expected: Validation error

## Decision Table

TC1: Existing username + incorrect password -> Error shown
TC2: Existing username + correct password -> Login successful
TC3: Nonexistent username + correct password -> Error shown
TC4: Nonexistent username + incorrect password -> Error shown

|   Conditions     |  TC1   |   TC2   |   TC3   |    TC4   |
|------------------|--------|---------|---------|----------|
| Username exists  |    T   |    T    |    F    |     F    |
| Password correct |    F   |    T    |    T    |     F    | 
| Actions          |        |         |         |          | 
|------------------|--------|---------|---------|----------|
| Log in success   |        |    X    |         |          |
| Error shown      |    X   |         |    X    |     X    |    

## State Transition (Follow/Unfollow)

|   Current State   |   Event      |	Next State  |
|-------------------|--------------|----------------|
|   Not Following	|Click Follow  |    Following   |
|   Following	    |Click Unfollow|   Not Following|
|   Not Following	|Click Unfollow|	Invalid     |
|   Following       |Click Follow  |	Invalid     |

|   Test Case   |   Initial State   |    Event     |   Expected Result                  |
|---------------|-------------------|--------------|------------------------------------|
| ST1           | Not Following     |Click Follow  | State changes to Following         |
| ST2           | Following         |Click Unfollow| State changes to Not Following     |
| ST3           | Not Following     |Click Unfollow|No state change; invalid transition |
| ST4           | Following         | Click Follow | No state change; invalid transition|