## Use Case: Fly to Destination

**ID**

SC7


**Description**

A UAV is tasked with flying to a remote specific set of coordinates.

**Invoked by**

| [River and Ice Rescue](../main/RiverRescue.md) | [Item Delivery](../main/ItemDelivery.md)| [AccidentSurveillance](../main/AccidentSurveillance.md) | [StructuralFire](../main/StructuralFire.md) | [EnvironmentalSampling](../main/EnvironmentalSampling.md) |
| :------: | :--------: | :--------: | :------: |:------: |
|   | x |  |  |  |

**Constraints**

The FAA requires a specific waiver to fly beyond visual line of sight (BVLOS), and UAVs must been stringent requirements. Without the BVLOS waiver, 
this use case is limited to flights within line of sight.  This use case differs from the basic flight to a waypoint that would be part of a local area search.
For example, we use it in conjunction with item delivery.  We write basic requirements here and will expand if BVLOS flights are feasible in the future.

**Primary Actor**

- Semi-Autonomous UAV

**Supporting Actors**

- Air Traffic Control

**Stakeholders and Interests**

- RPIC
- General public

**Pre-Conditions**

- The UAV is in the air 

- The UAV has been assigned target coordinates as its final destination

- The UAV has received [flight authorization](FlightAuthorization.md) to fly to its destination

**Post Conditions**

_Success end condition:_

The UAV arrives at its destination in a timely manner without incident

_Failure end condition:_

The UAV fails to arrive at its destination coordinates in a timely manner and/or experiences a collision with an obstacle or the terrain along the route.

**Trigger**

The UAV has been assigned a set of destination coordinates and has received flight authorization by the FAA.

## Main Success Scenario

1. DroneResponse decomposes the entire flight path into a series of `flight_legs`, each one with its own target waypoint.
2. DroneResponse establishes an initial altitude of the flight `[starting_altitude]` and assigns it as the starting altitude of each individual leg.
3. DroneResponse checks the starting `flight_leg` to ensure that it does not pass through any prohibited airspace whilst maintaining its `[starting_altitude]`.
4. DroneResponse uses a terrain map to check the altitude of the flight_leg's terrain to ensure that the UAV maintains `[minimum_terrain_separation]` whilst maintaining the `[starting_altitude]` of the current leg.
5. Steps 3-4 are repeated for each `flight_leg`. 
6. Given the flight plan, the UAV checks that it has sufficient battery power to reach its destination and determines that it has sufficient power to continue.
7. The UAV [leases airspace](../supporting/LeaseAirspace.md] for the current flight leg.
8. The UAV ascends or descends to the target altitude of the current flight leg.
9. The UAV flies to the destination waypoint of the current flight leg.
10. The UAV reports its arrival at the flight leg's destination waypoint.
11. Steps 6-8 are repeated until the UAV reaches its final destination.
12. The use cases finishes when the UAV assumes the task assigned for it to do at its final destination.

## Exceptions

1. All [general exceptions](../../README.md#GeneralExceptions) apply.

2. In step 6, the UAV determines that it lacks sufficient battery power to complete the mission.
   * 2.1 The UAV notifies the human operator and awaits further instructions.

3. In steps 2 or 3 it is determined that the UAV will pass through prohibited airspace.
   * 3.1 An alternate flight path is planned around the prohibited airspace and/or at a new altitude
   * 3.2 If necessary, the flight path is divided into a series of waypoints representing multiple `flight_legs`
   * 3.3 Steps 2 and 3 are repeated until a viable flight path is found.
      * 3.3.1 If no viable flight path can be found the operator is notified and the flight is cancelled.
	  * 3.3.1 If a viable flight path is found, then original series of `flight_legs` is updated with the modified legs

4. In step 6, has been assigned a task that requires additional battery power (e.g., return to home coordinates, survey the landscape). 
   * 4.1 The UAV estimates power requirements for completing the entire task.
   * 4.2 If a return home is required, the UAV estimates power requirements for returning home.
   * 4.3 The UAV estimates total battery requirements required and determines whether it can complete the entire mission.
      * 4.3.1 The UAV determines that it has sufficient power to complete the entire mission and the use case continues with steps 7-11.
	  * 4.3.2 The UAV determines that it lacks sufficient power to complete the entire mission and Exception Use-Case #2 is executed.

5. In step 7, the UAV is unable to lease the requested airspace after several attempts.
   * 5.1 The UAV notifies the operator that it was unable to lease airspace for the planned flight.
   * 5.2 The operator decides how to respond and either:
      * 5.2.1 Replans the route and the use case continues at step 7.
      * 5.2.2 Cancels the mission
 

[Return to use case list](../../README.md)
