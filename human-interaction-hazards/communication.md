## Hazard Tree: Communication (or will be soon!)

One of the most common causes of accidents with sUAS is caused by loss-of-signal preventing the RPIC from sending commands to the sUAS or receiving status updates. RPICs communicate with their sUAS by sending commands through a hand-held controller (i.e., throttle, forward, backward, sideways, turn) or through use of a computer system (e.g., MissionPlanner, QGroundControl, or custom built software) operating over an alternate communication technique or frequency.  Hazard mitigations are dependent upon the operating context -- specifically whether redundant communication paths exist, and whether the loss of signal is caused by a fault on the UAV or a communication failure. 

[![](figures/communication.png)](#)

Quick Links: [UX1](#UX1) [UX2](#UX2) [UX3](#UX3) [UX4](#UX4) [UX5](#UX5) [home](../README.md)

## <a name="GX1">CX1: The human operator is unable to communicate with the UAV via the hand-held controller</a>

One way RPICs communicate with their sUAS by sending commands through a hand-held controller (i.e., throttle, forward, backward, sideways, turn). In environments where the sUAS is controlled by a computer software system, the hand-held controller provides a backup system for taking manual control when problems occur.

| Hazard addressed | Context | Solution |
|:--|:--|:--|
|UX1-1|Hand-held controller is the only remote control mechanism.|The RPIC is unable to send commands to the sUAV. They need to be aware of onboard mitigations (geofence, failsafe), consider the operating environment (urban vs. rural area, controlled airspace etc), so that they can make an informed decision about whether to immediately report the fly-away event. 
|UX1-2|Redundant controllers exist (i.e., hand-held + computer system) and the operator is using the hand-held device because communication from the computer has also failed | As in the previous example, the RPICs needs situational awareness of onboard mitigations (e.g., geofence location and configurations, failsafe mechanisms). This information should be cached in the ground-based computer immediately following initial configuration so that it can be displayed upon request when signal is lost. 


## <a name="GX2">GX2: Operator ignores prohibited airspace warnings and flies into prohibited airspace</a>

There are also accounts of RPICs deliberately flying in prohibited airspace. 
| Hazard addressed | Solution |
|:--|:--|
|GX2-1|When a flight path is planned into prohibited airspace, the flight will be blocked until the RPIC acknowledge the warning and issues an override |
|GX2-2|All overrides issued by the RPIC are logged in a persistent transaction file|

## <a name="GX3">GX3: Operator fails to establish appropriate geofence prior to flight</a>

Many prohibited flight areas will not appear on the map as a result of retrieving LANNC data.  For example, in the USA, RPIC are not permitted to fly their UAVs over people which includes flying over traffic.  Furthermore, incursions into prohibited airspace can be caused by signal loss and onboard mechanical failures resulting in fly-away events. Several of these problems can be prevented by establishing a geofence; however, many current UAV flight systems do not require geofences and RPICs may fail to check this.

| Hazard addressed | Solution |
|:--|:--|
|GX3-1|If a geofence is not activated for the current location (region and altitude) then a warning will be generated|
|GX3-2|When the UAV is connected to the system, its geofence is retrieved and shown on the map until dismissed by the RPIC|
|GX3-3|If a flight plan would cause the UAV to fly outside the geofence, then a warning will be generated|
|GX3-4|If the RPIC is coordinating multiple UAVs (either with a part 107 waiver or in conjunction with multiple RPIC operators), then the system must allow the RPIC to set the geofences of all or several UAVs at the same time.

## <a name="GX4">GX4: Operator sets the geofence failsafe parameters incorrectly, and the UAV flies beyond the geofence boundary</a>

When a UAV approaches the geofence its onboard failsafe mechanisms will activate.  These typically are either LAND or RTL. The operator must ensure that failsafe mechanisms are configured correctly.

| Hazard addressed | Solution |
|:--|:--|
|GX4-1|When the geofence is displayed, the default failsafe mechanisms will also be displayed on the screen.  These include actions (LAND, RTL) and distance from the geofence at which the mechanisms will be activated.
|GX3-2|If the RPIC is coordinating multiple UAVs (either with a part 107 waiver or in conjunction with multiple RPIC operators), then the system must allow the RPIC to configure  geofence failsafe mechanismas for all or several UAVs at the same time.

