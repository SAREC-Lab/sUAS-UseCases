## Hazard Tree: Hardware and Sensors

**Description**

Human technicians are responsible for setting up hardware (e.g., sensors, UAV), while the RPIC is responsible 
for preflight inspections and for handling runtime faults as they occur. 

[![](figures/sensors.png)](#)


Return to [hazard list](../README.md)<br>



 <sub>[![](icons/h-icon.PNG)](#)</sub> = Human initiated error,  <sub>[![](icons/s-icon.PNG)](#)</sub> =Loss of Situational awareness,  <sub>[![](icons/e-icon.PNG)](#)</sub> = Lack of empowerment to intervene
 
 ## Human-Drone Interaction Hazards 

###  <sub>[![](icons/e-icon.PNG)](#)</sub> SX1: The UAV hovers in the sky and is unresponsive to operator commands
| <img width=120/>| Context | Solution |
|:--|:--|:--|
|SX1-S1|In-Air|The position and expected behavior of the UAV shall be monitored continuously. If a UAV does not behave accoring to its last command (e.g., not moving when ordered to fly to a waypoint), the system shall display a warning message and suggest to re-send the previous command.|
|SX1-S2|In-Air|In case of an unresponsive UAV the RPIC shall switch to the backup control (e.g. hand-held) and issue either an RTL command or a land in place command if the UAV can be landed safely at its corrent location. |

<br><br>

###  <sub>[![](icons/e-icon.PNG)](#)</sub> SX2: The UAV flies out of control and does not respond to operator commands
|  <img width=120/> | Context | Solution |
|:--|:--|:--|
|SX2-S1|In-Air|If the operator experiences loss-of-control they can trigger an emergency alert|
|SX2-S2|In-Air,Active onboard analytics|Where onboard analytics are active and a deviation between commands and response are detected, the system issues a loss-of-control warning|
|SX2-S3|In-Air, Multi-UAVs|Where multiple UAVs are flying in the locality of the uncontrolled UAV, a zone-avoidance warning is immediately broadcast around the uncontrolled zone|

<br><br>

###   <sub>[![](icons/s-icon.PNG)](#)</sub> SX3: The operator is not immediately aware that hardware has failed
|  <img width=120/> | Context | Solution |
|:--|:--|:--|
|SX3-S1|All|The runtime monitor shall continually check the health of critical hardware components and raise alerts when they fail.|

<br><br>

###  <sub>[![](icons/e-icon.PNG)](#)</sub> SX4: The operator is unable to evaluate the severity of the geolocation problem and/or resolve the situation.
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|SX4-S1|Inflight|On onboard companion computer provides camera diagnostic capabilities and reports any detected errors and their severity to the operator|

<br><br>

###  <sub>[![](icons/s-icon.PNG)](#)</sub> SX5: The operator loses track of the UAV's geolocation
|  <img width=120/> | Context | Solution |
|:--|:--|:--|
|SX5-S1|Inflight|When the UAV's geolocation becomes uncertain due to loss of satellite or other detectable errors, current uncertainty of the UAV's position shall be depicted on the UI (e.g., through an ever enlarging circle representing the predicted location of the UAV).|

<br><br>

###  <sub>[![](icons/s-icon.PNG)](#)</sub> SX6: The camera that provides video stream and supports onboard vision becomes unavailable to the operator when they need it to support the mission
|  <img width=120/> | Context | Solution |
|:--|:--|:--|
|SX6-S1|Inflight|The system supports a remote camera reset function|
|SX6-S2|Multi-UAV,Inflight|The system allows the operator to request a replacement UAV by recalling the UAV with the non-functioning camera and replacing it with another UAV (airborne or on the ground) with a functioning camera)|

<br><br>

###  <sub>[![](icons/h-icon.PNG)](#)</sub> SX7: The operator accidientially deploys the parachute during flight
|  <img width=120/> | Context | Solution |
|:--|:--|:--|



