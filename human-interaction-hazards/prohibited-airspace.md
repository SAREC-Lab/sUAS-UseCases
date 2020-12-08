## Hazard Tree: Regulatory compliance

UAV flights must be in compliance with government and local ordinances and regulations. In the USA all commercial pilots must seek authorization for flights in controlled airspace.

[![](figures/regulatory-compliance.png)](#)

Quick Links: [GX1](#GX1) [GX2](#GX2) [GX3](#GX3) [GX4](#GX4) [(All Hazards)](../README.md)<br>

<sub>![](icons/h.png)</sub> = Human initiated error, <sub>![](icons/s.png)</sub> =Loss of Situational awareness, <sub>![](icons/e.png)</sub> = Lack of empowerment to intervene

## GX1-GX4: I think we should list these together.  It is really "just don't do it!!"

There are numerous accounts of remote pilots either accidentally flying their UAVs into prohibited airspace.  This is particularly common around airports.

| Hazard addressed | Solution |
|:--|:--|
|GX1-1|Data describing all prohibited airspace in the vicinity must be retrieved and displayed visually on the map |
|GX1-2|Warnings must be issued if any flight plan creates an incursion into prohibited airspace |

## <a name="GX2">GX2: Operator ignores prohibited airspace warnings and flies into prohibited airspace</a> <sub><sup>:one:</sup></sub>

There are also accounts of RPICs deliberately flying in prohibited airspace. 
| Hazard addressed | Solution |
|:--|:--|
|GX2-1|When a flight path is planned into prohibited airspace, the flight will be blocked until the RPIC acknowledge the warning and issues an override |
|GX2-2|All overrides issued by the RPIC are logged in a persistent transaction file|

## <a name="GX3">GX3: Operator fails to establish appropriate geofence prior to flight</a> <sub><sup>:one:</sup></sub>

Many prohibited flight areas will not appear on the map as a result of retrieving LANNC data.  For example, in the USA, RPIC are not permitted to fly their UAVs over people which includes flying over traffic.  Furthermore, incursions into prohibited airspace can be caused by signal loss and onboard mechanical failures resulting in fly-away events. Several of these problems can be prevented by establishing a geofence; however, many current UAV flight systems do not require geofences and RPICs may fail to check this.

| Hazard addressed | Solution |
|:--|:--|
|GX3-1|When a geofence is not activated for the current location (region and altitude) a warning shall be generated|
|GX3-2|As soon as the UAV is connected to the system, the UAV's existing geofence data shall be retrieved and visibly displayed on the map until dismissed by the RPIC|
|GX3-3|When a planned flight extends outside the geofence a warning will be generated|
|GX3-4|Where an RPIC is coordinating multiple UAVs (either with a part 107 waiver or in conjunction with multiple RPIC operators), then the system must allow the RPIC to set the geofences of all or several UAVs at the same time.

## <a name="GX4">GX4: Operator sets the geofence failsafe parameters incorrectly, and the UAV flies beyond the geofence boundary</a> <sub><sup>:one:</sup></sub>

When a UAV approaches the geofence its onboard failsafe mechanisms will activate.  These typically are either LAND or RTL. The operator must ensure that failsafe mechanisms are configured correctly.

| Hazard addressed | Solution |
|:--|:--|
|GX4-1|When the geofence is displayed, the default failsafe mechanisms will also be displayed on the screen.  These include actions (LAND, RTL) and distance from the geofence at which the mechanisms will be activated.
|GX4-2|Where the RPIC is coordinating multiple UAVs (either with a part 107 waiver or in conjunction with multiple RPIC operators), then the system must allow the RPIC to configure  geofence failsafe mechanisms for multiple UAVs simultaneously.

