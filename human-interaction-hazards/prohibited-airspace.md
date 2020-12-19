# Hazard Tree: Regulatory Compliance

**Description** 

UAV flights must be in compliance with government and local ordinances and regulations. In the USA all commercial pilots must seek authorization for flights in controlled airspace. Activities such as logging or sharing data with the NASA infrastructure all serve to support compliance and safety, but exhibit clear tradeoffs against privacy. 


[![](figures/regulatorycompliance.png)](#)


<sub>![](icons/h-icon.PNG)</sub> = Human Initiated Error, <sub>![](icons/s-icon.PNG)</sub> = Loss of Situational awareness, <sub>![](icons/e-icon.PNG)</sub> = Lack of Empowerment to Intervene

Return to [hazard list](../README.md)<br>

## Human-Drone Interaction Hazards

### <a name="GX1"> <sub>![](icons/h-icon.PNG)</sub> GX1: The system is unable to connect to the LANNC system but the RPIC flies anyway 
  
All RPICs flying in controlled airspace must receive flight authorization from the LANNC system via a third-party application (e.g., AirMap). Flying in controlled airspace without authorization is reckless and illegal.  However, flight authorization may have been obtained in advance, acquired directly from ATC at a local airport, or requested immediately prior to the flight. 
|<img width=120/>|Context| Solution |
|:--|:--|:--|
|GX1-S1|Preflight|When the system is unable to connect to the LANNCs prior to a flight, a warning message should be prominently displayed on the screen.| 
|GX1-S2|Preflight|If authorization has been received prior to the flight, or the RPIC is operating under a waiver, the warning is disabled when the RPIC confirms that they are flying under prior authorization. |
|GX1-S3|Preflight|If the RPIC attempts to arm and takeoff without authorization the RPIC is required to explicitly acknowledge the warning, and this acknowledgement is logged.|

<br><br>

### <a name="GX2"> <sub>![](icons/h-icon.PNG)</sub> GX2: Flight authorizations is denied by the LAANC system, but the RPIC flies anyway 
All RPICs flying in controlled airspace must receive flight authorization from the LANNC system via a third party (e.g., AirMap).  Flying in controlled airspace without authorization is reckless and illegal.  When flight authorization is denied, the RPIC may modify the request and resubmit. 
|<img width=120/>|Context| Solution |
|:--|:--|:--|
|GX2-S1|Preflight|When flight authorization is denied a warning message must be prominently displayed on the screen.| 
|GX2-S2|Preflight|If the RPIC attempts to arm and takeoff without authorization the RPIC is required to explicitly acknowledge the warning, and this acknowledgement is logged.|

<br><br>

### <a name="GX3"> <sub>![](icons/h-icon.PNG)</sub> GX3: The operator recklessly disregards FAA flying regulations without a Part 107 waiver
All of these hazards relate to reckless behavior as defined by Part 107 regulations
|<img width=120/>|Context| Solution |
|:--|:--|:--|
|GX3-S1|System|The system should provide an explicit reminder which requires acknowledgement to fly responsibly in compliance with FAA regulations on the start-up screen.|
|GX3-S2|System|The system provides an external link to a page listing FAA regulations. |
|GX3-S3|System|The system stores Part 107 certification numbers in the system for frequent commercial RPICs. |
|GX3-S4|System|The system creates a dedicated log-file for each flight that logs meta-data including time of day, any infringements upon authorized airspace, and the RPIC of record. |

### <sub>![](icons/h-icon.PNG)</sub> GX4: The operator releases the UAV from a moving vehicle in a populated area
See GX3
<br><br>

### <sub>![](icons/h-icon.PNG)</sub> GX5: The operator flies over people without a regulatory waiver
See GX3
<br><br>

### <a name="GX7"> <sub>![](icons/s-icon.PNG)</sub> GX7: Operator is unaware of prohibited airspace and plans and/or executes illegal flight routes
|<img width=120/>|Context| Solution |
|:--|:--|:--|
|GX7-S1|System|Data describing all prohibited airspace in the vicinity must be retrieved and displayed visually on the map. |
|GX7-S2|Prelaunch|Warnings must be issued if any planned flight would create an incursion into prohibited airspace. |
|GX7-S3|Prelaunch|Before takeoff the RPIC must explicitly confirm the planned route and routes and confirmations are logged by the system. |
|GX7-S4|System|Situational awareness demons related to information overload and misplaced salience must be addressed through principled design and user evaluations. |

<br><br>

### <a name="GX8"> <sub>![](icons/h-icon.PNG)</sub> GX8: Operator ignores warnings about prohibited airspace 
|<img width=120/>|Context| Solution |
|:--|:--|:--|
|GX8-S1|System|Incursions into prohibited airspace must be logged|

<br><br><br><br>

### <sub>![](icons/e-icon.PNG)</sub> GX12: Routes are automatically generated for a specific area without considering prohibited airspace 
|<img width=120/>|Context| Solution |
|:--|:--|:--|
|GX9-S1|Pelaunch|Before assigning a route to a UAV, the system checks for each automatically generated route if the route intersects with a no-fly zone.   |

