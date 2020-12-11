## Hazard Tree: Flight Collisions

Collisions must be avoided between multiple UAVs, UAVs and other objects, and UAVs and the terrain.

[![](figures/collisions.png)](#)

Quick Links: [FX1](#FX1) [FX2](#FX2) [FX3](#FX3) [FX4](#FX4) [FX5](#FX5)   [(All Hazards)](../README.md)<br>

<sub>![](icons/h-icon.PNG)</sub> = Human initiated error, <sub>![](icons/s-icon.PNG)</sub> =Loss of Situational awareness, <sub>![](icons/e-icon.PNG)</sub> = Lack of empowerment to intervene


##  <sub>![](icons/s-icon.PNG)</sub> FX1: The operator is unaware that the UAV is flying too close to the terrain

| <img width=150/> | Context | Solution |
|:--|:--|:--|
|FX1-S1| In-Air | When falling below a minimum threshold altitude, the system shall automatically display a warning message, notifying the RPIC. |
|FX1-S2| In-Air | When falling below a critical threshold altitude, the system shall notify the RPIC that it will automatically initiate an ascending procedure to the minimum safe altitude. The RPIC can override the ascending if the UAV should stay at the lower altitude. This override should be logged in the flight log. |

##  <sub>![](icons/e-icon.PNG)</sub> FX2: The operator has no means of overriding the onboard autonomy and/or cannot do so quickly enough in order to avoid a collision with the terrain

| <img width=150/> | Context | Solution |
|:--|:--|:--|
|FX1-1|Context here| Mitigation here|

##  <sub>![](icons/s-icon.PNG)</sub> FX3: The operator is unaware that GPS accuracy is degraded and that UAVs are in danger of mid-air collisions.

| <img width=150/> | Context | Solution |
|:--|:--|:--|
|FX3-S1| In-Air | If the number of locked sattelites falls below a threshold, the system shall automatically display a warning message, notifying the RPIC. The position inaccuracy shall be displayed in the user interface, e.g. by displaying a circle around the UAV, showing its approx. estimated position.  |

##  <sub>![](icons/h-icon.PNG)</sub> FX4: The technician has assigned the same RTL altitude for multiple UAVs | See preflight configuration 

| <img width=150/> | Context | Solution |
|:--|:--|:--|
|FX1-1|Context here| Mitigation here|

##  <sub>![](icons/e-icon.PNG)</sub> FX5: The handover of control from the computerized system to a manual operator results in uncontrollable flight

| <img width=150/> | Context | Solution |
|:--|:--|:--|
|FX1-1|Context here| Mitigation here|

##  <sub>![](icons/h-icon.PNG)</sub> FX6: When the operator assumes manual control during the mission and switches (e.g., throttle) are set incorrectly, the UAV responds dramatically (e.g., plunging to the ground). 

| <img width=150/> | Context | Solution |
|:--|:--|:--|
|FX1-1|Context here| Mitigation here|

##  <sub>![](icons/s-icon.PNG)</sub> FX7: The operator is unaware that the switches are set incorrectly.

| <img width=150/> | Context | Solution |
|:--|:--|:--|
|FX7-S1|Preflight| Training and respective preflight checks shall be introduced that check switch positions before the UAV can arm and take-off. |

##  <sub>![](icons/s-icon.PNG)</sub> FX8: When the operator assumes manual control of the UAV, they do not know how the UAV is oriented (i.e., which direction the UAV is facing) and find it difficult to immediately control the UAV.

| <img width=150/> | Context | Solution |
|:--|:--|:--|
|FX1-1|Context here| Mitigation here|
