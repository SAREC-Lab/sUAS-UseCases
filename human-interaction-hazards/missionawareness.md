## Hazard Tree:  Mission Awareness

[![](figures/missionawareness.png)](#)

<sub>![](icons/h-icon.PNG)</sub> = Human Initiated Error, <sub>![](icons/s-icon.PNG)</sub> = Loss of Situational awareness, <sub>![](icons/e-icon.PNG)</sub> = Lack of Empowerment to Intervene

Return to [hazard list](../README.md)<br>

## Human-Drone Interaction Hazards 

### <sub>[![](icons/e-icon.PNG)](#)</sub> AX1: The operator is unable to handle multiple alerts simultaneously

| Hazard addressed | Context | Solution |
|:--|:--|:--|
|AX1-S1|Multiple sUAS in flight|Alerts must be prioritized according to severity|
|AX1-S2|Multiple sUAS in flight|When system-wide failures occur the operator can freeze the entire mission so that all sUAS are commanded to hover in place. This gives the RPIC time to plan recovery strategies and/or to manually issue RTL or LAND commands to individual sUAS.|

<br><br>

### <sub>[![](icons/s-icon.PNG)](#)</sub> AX2: The operator is overwhelmed by status information for multiple UAVs.</a>

| Hazard addressed | Context | Solution |
|:--|:--|:--|
|AX2-S1 |Active mission |UI must be designed to avoid information overload by careful prioritization of alerts|
|AX2-S2 |Active mission |Only critical status data shall be displayed continously, whilst other information shall be displayed upon request. (For example: display latitude and longitude upon demand and replace with velocity and a directional arrow). 

<br><br>

### <sub>[![](icons/s-icon.PNG)](#)</sub> AX3: The operator becomes overwhelmed by the multi-tasking required to manage multiple UAVs safely and according to all regulations

| Hazard addressed | Context | Solution |
|:--|:--|:--|
|AX3-S1 |Multi-UAVs |Where feasible automate the behavior of UAVs so that they can execute autonomously.|

<br><br>

### <sub>[![](icons/s-icon.PNG)](#)</sub> AX4: The operator focuses excessively on one aspect of the mission at the expense of other aspects (e.g., focuses on finding the victim but ignores safe UAV operation)

| Hazard addressed | Context | Solution |
|:--|:--|:--|
|AX4-S1|Multiple human engagers | One operator is designated as the sUAS safety officer with primary responsibility for overseeing safe use of the sUAS. |
|AX4-S2|Multiple human engagers | The UI provides a screen dedicated to sUAS command and control. |
|AX4-S3|Multiple sUAS| System runtime monitoring constantly checks for safety violations and raises alerts when such violations occur.|

<br><br>

### <sub>[![](icons/s-icon.PNG)](#)</sub> AX5: The operator has an incorrect (errant) mental model of the current environment

| Hazard addressed | Context | Solution |
|:--|:--|:--|
|AX5-S1 |Active mission|Provide visual clues about the current mission context (e.g., excessively cold temperature, high winds, poor lighting)|

<br><br>

### <sub>[![](icons/s-icon.PNG)](#)</sub> AX6: The operator does not understand important characteristics of the current environment and how they might impact the UAVs and/or the mission

| Hazard addressed | Context | Solution |
|:--|:--|:--|
|AX6-S1 |Active mission|When requested by the user, provide explanations of the potential impact of off-nominal conditions upon the mission (e.g., Extreme cold conditions could impact controllability of the UAV, or using RGB camera during dusk could result in low accuracy of onboard vision).|

<br><br>

### <sub>[![](icons/h-icon.PNG)](#)</sub> AX7: The operator lacks experience flying in current conditions
| Hazard addressed | Context | Solution |
|:--|:--|:--|
See AX5, AX6

<br><br>

### <sub>[![](icons/s-icon.PNG)](#)</sub> AX8: The operator goes out of the loop due to UAV autonomy

| Hazard addressed | Context | Solution |
|:--|:--|:--|
|AX8-S1|Active Mission|Provide active alerts when UAV makes a significant autonomous decision (e.g,. transitions from search to tracking mode).
|AX8-S2|Active Mission|When the operator is required to intervene, provide visual and audible alerts and a clear directive of their required intervention.|
|AX8-S3|Active Mission|When the operator needs to take manual control but is unsure of the direction in which the UAV is facing, they may request that the UAV autonomously turns to face them.|

<br><br>

### <sub>[![](icons/s-icon.PNG)](#)</sub> AX9: The operator fails to understand autonomous decisions

| Hazard addressed | Context | Solution |
|:--|:--|:--|
|AX9-S1 |Multi-UAVs |Make explanations of UAVs' autonomous decisions available to the operator upon request or at the time the autonomous event occurs.|

<br><br>

### <sub>[![](icons/s-icon.PNG)](#)</sub> AX10: The operator fails to recognize when a UAV is operating autonomously outside its safety envelope

| Hazard addressed | Context | Solution |
|:--|:--|:--|
|AX10-S1 |Active Mission |Establish constraints on the safe operating space of the UAV, monitor for violations of those constraints, and clearly warn the operator when the UAV is operating outside its safety envelope.|

<br><br>

### <sub>[![](icons/h-icon.PNG)](#)</sub> AX11: The operator fails to supervise the UAVs due to excessive trust in autonomy

| Hazard addressed | Context | Solution |
|:--|:--|:--|
See AX8
