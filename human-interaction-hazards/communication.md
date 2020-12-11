# Hazard Tree: Communication

**Description** 

One of the most common causes of accidents with sUAS is caused by loss-of-signal preventing the RPIC from sending commands to the sUAS or receiving status updates. RPICs communicate with their sUAS by sending commands through a __hand-held-controller__ (i.e., throttle, forward, backward, sideways, turn) or through use of a computer system (e.g., MissionPlanner, QGroundControl, or custom built software) operating over an alternate communication technique or frequency.  Hazard mitigations are dependent upon the operating context -- specifically whether redundant communication paths exist, and whether the loss of signal is caused by a fault on the UAV or a communication failure. 


Quick Links: [CX1](#CX1) &nbsp;&nbsp; [CX2](#CX2) &nbsp;&nbsp; [CX3](#CX3) &nbsp;&nbsp; [CX4](#CX4) &nbsp;&nbsp; [CX5](#CX5) &nbsp;&nbsp; [(All Hazards)](../README.md)<br>

<sub>![](icons/h-icon.PNG)</sub> = Human Initiated Error, <sub>![](icons/s-icon.PNG)</sub> =Loss of Situational Awareness, <sub>![](icons/e-icon.PNG)</sub> = Lack of Empowerment to Intervene

##  <sub>![](icons/e-icon.PNG)</sub> <a name="CX1"> CX1: The human operator is unable to communicate with the UAV via the hand-held controller</a> 

One way RPICs communicate with their sUAS by sending commands through a hand-held controller (i.e., throttle, forward, backward, sideways, turn). In environments where the UAV is controlled by a software system, the hand-held controller provides a backup system for taking manual control when problems occur.

| <img width=150/> | Context | Solution |
|:--|:--|:--|
|CX1-S1|Hand-held controller is the only remote control mechanism.|The RPIC is unable to send commands to the UAV. They need to be aware of onboard mitigations (geofence, failsafe), consider the operating environment (urban vs. rural area, controlled airspace etc), so that they can make an informed decision about whether to immediately report the fly-away event. 
|CX1-S2|Redundant controllers exist (i.e., hand-held + software system) and the operator is using the hand-held device because communication from the software system has failed. |As in the previous example, the RPICs needs situational awareness of onboard mitigations (e.g., geofence location and configurations, failsafe mechanisms). This information should be cached in the ground-based computer immediately following initial configuration so that it can be retrieved upon request|
|CX1-S3|Same context as CX1-S2|The UI must provide the capability to display the cached geofence, failsafe mechanisms, and their configurations upon demand|

## <sub>![](icons/s-icon.PNG)</sub> <a name="CX2">CX2: The human operator is unable to receive status data from the UAVs using the software-based system.</a>

Due to loss of signal no data is transmitted from the UAV.
| <img width=120/> | Context | Solution |
|:--|:--|:--|
|CX2-S1|UAV status is normally depicted in the UI |The approximate position and the uncertainty of the UAV's current position on the map must be visually depicted (e.g., by creating an increasingly large 'circle' around the last known, or projected position of the UAV|
|CX2-S3|Same as CX2-S1|An indicator (e.g., an icon or flashing text) must communicate that communication is lost|
|CX2-S3|Same as CX2-S1|Information should be provided in the UI on how much time since the last contact with the UAV has elapsed. |
|CX2-S4|Same as CX2-S1|Each loss of signal must be logged in the respective flight log (including time of occurence and duration of the signal loss). |

## <sub>![](icons/e-icon.PNG)</sub> <a name="CX3">CX3: The human operator is unable to send directives to the UAV using the software-based system</a> 

| <img width=120/> | Context | Solution |
|:--|:--|:--|
|CX3-S1|The software system is the only remote control mechanism.|The RPIC is unable to send commands to the UAV. They need to be aware of onboard mitigations (geofence, failsafe), consider the operating environment (urban vs. rural area, controlled airspace etc), so that they can make an informed decision about whether to immediately report the fly-away event. 
|CX3-S2|A hand-held redundant controller is available |The system reports loss of signal and the human operator attempts to take over manual control using the hand-held controller|

##  <sub>![](icons/e-icon.PNG)</sub> <a name="CX4">CX4: The operator cannot rely on forwarding of messages to remote UAVs via UAV-to-UAV messaging</a>

When in-air communication infrastructure fails the operator may need to communicate directly with each individual UAV

| <img width=120/> | Context | Solution |
|:--|:--|:--|
|CX4-S1|In-air communication infrastructure| A warning must be display notifying the operator that in-air messaging is offline.
|CX4-S2|Same as CX4-S1|Loss loss of in-air messaging must be logged in the respective flight log (including time of occurence and duration of the communication loss).

## <sub>![](icons/s-icon.PNG)</sub> <a name="CX5">CX5: The human operator lacks understanding of the nature of the communication problem</a> 

The operator may observe that communication has failed, or perceive it to have failed, without understanding the nature of the problem (e.g., malicious jamming attack, interference, loss of LTE connection). In order for the RPIC to respond correctly to the situation, they need to be able to quickly diagnose the problem.

| <img width=120/> | Context | Solution |
|:--|:--|:--|
|CX5-S1|All|A dedicated runtime monitoring component shall constantly monitor the health of individual components, detect failures, and provide diagnostic reports to the user when individual parts of the system fail (e.g., GCS is connected but not receiving signals from UAV.|
|CX5-S2|Multiple communication options | Where multiple communication technologies are available (e.g., LTE vs. telemetry vs. wifi), the system shall perform diagnostics, switch to the most reliable approach, and notify the user of the current state of communicaiton.|


