## Use Case: Flight authorization from Aviation Regulators

**Description**

Request flight authorization

**Invoked by**

[IceRescue](../main/IceRescue.md), [RiverRescue](../main/RiverRescue.md), [AccidentSurveillance](../main/AccidentSurveillance.md), [AirSampling](../main/AirSampling.md), [WaterSampling](../main/WaterSampling.md), [DefibrillatorDelivery](../main/DefibrillatorDelivery.md), [StructuralFire](../main/StructuralFire.md)

**Primary Actor**

RPIC

**Supporting Actors**

Semi-autonomous UAV

**Stakeholders and Interests**

- FAA
- NASA
- General public

**Pre-Conditions**

- Authorization service is available
- Flight routes and region is known

**Post Conditions**

Success end condition

- UAV is authorized to fly or authorization is denied for a valid reason

Failure end condition:

- UAV flies without authorization or flies outside of authorized limits

**Trigger**

- Flight routes are planned for current or future mission


## Main Success Scenario

1. The RPIC visually inspects all UAVs prior to takeoff to ensure their flight-worthiness.
2. The RPIC checks weather conditions for visibility (3 miles), temperature (must be within operating range of the UAV), and other conditions such as wind and precipitation to ensure safe flight.
3. For each UAV flying in FAA controlled airspace, DroneResponse prepares an authorization request containing the UAV's registration, flight time, and flight region.
4. DroneResponse connects to an authorization service provider (e.g., AirMap) and requests authorization for a UAV's valid flight plan.
5. AirMap returns permission to fly including airspace constraints such as altitude limits and no-fly zones.
6. DroneResponse marks all airspace restriction on the map.  All subsequent flight paths are checked against these restrictions prior to, and during, each flight.
7. DroneResponse establishes a geofence that matches the outer boundary of the region for which flight authorization has been received.

## Exceptions

1. In step 1, the RPIC deems that a UAV is not flight-worthy.
   * 1.1 Where feasible, corrections are made to the UAV so that it passes the flight-worthiness test.
   * 1.2 Any UAV that is not deemed flight-worthy is removed from the mission.
   
2. In step 2, the RPIC deems weather conditions are unsafe for flight and the mission is aborted.
   
3. In step 3, flight authorization is requested for an invalid flight plan e.g., (i) nighttime flight (without a waiver), (ii)flying in permanently or temporarily prohibited airspace
   * 3.2 Flight authorization is denied.
   * 3.3 The RPIC either aborts the mission or replans a valid mission and resubmits a new flight plan.
   
4. In steps 3 or 4, Airmap fails to respond.
   * 4.1 Steps 2 and 3 are repeated at one minute periods until a response is received or three attempts have been made.
      * 4.1.1 In step 2.1 if no response is received the RPIC manually calls the local Air Traffic Control tower to seek flying permission.
	  * 4.1.2 If permission is received verbally, then the RPIC records this note in the DroneResponse system and the flight proceeds as authorized.
	  * 4.1.3 If permission is not granted by ATC or AirMap, then the flight is aborted.

5. In steps 3-5 the RPIC has a waiver to fly without prior authorization typically due to an emergency response authorization.
   * 5.1 Steps 3-6 are executed in parallel to launching the mission.
   
[Return to use case list](../../README.md)
