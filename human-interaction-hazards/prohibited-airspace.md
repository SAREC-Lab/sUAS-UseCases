## Hazard Tree: Prohibited Airspace

UAV flights must be in compliance with government and local ordinances and regulations. In the USA all commercial pilots must seek authorization for flights in controlled airspace.

[![](figures/airspace.png)](#)

Quick Links: [GX1](#GX1) [GX2](#GX2) [GX3]() [GX4]()

## <a name="GX1">GX1: Operator is unaware of prohibited airspace and plans illegal flight routes</a>

There are numerous accounts of remote pilots either accidentally flying their UAVs into prohibited airspace.  This is particularly common around airports.

| Hazard addressed | Solution |
|:--|:--|
|GX1-1|LANNC data, including all prohibited airspace in the vicinity must be retrieved and displayed clearly on the map |
|GX1-2|Warnings must be issued if any flight plan creates an incursion into prohibited airspace |

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
