## Use Case: Synchronized Takeoff

**ID**

SC11


**Description**

A cohort of UAVs takeoff and fly to initial waypoints using coordinated flight paths

**Invoked by**


| [River and Ice Rescue](../main/RiverRescue.md) | [Item Delivery](../main/ItemDelivery.md)| [AccidentSurveillance](../main/AccidentSurveillance.md) | [StructuralFire](../main/StructuralFire.md) | [EnvironmentalSampling](../main/EnvironmentalSampling.md) |
| :------: | :--------: | :--------: | :------: |:------: |
| x | x | x | x | x|

**Rationale**
Synchronized takeoff is needed so that UAVs don&#39;t collide when they take off and potentially cross paths on their way to their initial waypoints.

**Primary Actor**

- Semi-Autonomous UAV

**Supporting Actors**

- Drone Commander

**Stakeholders and Interests**

**Pre-Conditions**

- Each UAV is on the ground ready to takeoff
- Each UAV has been assigned a unique starting waypoint a minimum_separation_distance to all other UAVs

**Post Conditions**

_Success end condition:_

Each UAV reaches its initial waypoint without collision

_Failure end condition:_
 Collision occurs at takeoff or during flight to initial waypoints

**Trigger**

The UAVs receive the start mission command.

## Main Success Scenario

1. DroneResponse assigns each UAV an altitude between 20 feet and the maximum allowed altitude of the current flight area. Each altitude is separated by `_minimum\_separation\_distance_` from all other UAVs.
2. Each UAV takes off to its prescribed altitude and waits for all other UAVs to reach their altitudes.
3. Each UAV flies at its unique altitude to the longitude and latitude coordinates of its first waypoints. It waits for confirmation that all other UAVs have reached their designated coordinates.
4. Each UAV then descends or ascends to the designated altitude of its first waypoint and awaits confirmation that all other UAVs have reached their designated altitudes.

## Exceptions
1. All [general exceptions](../../README.md#GeneralExceptions) apply.

2. There is insufficient flying altitude to create safe separation between lanes for the number of UAVs involved in the synchronized takeoff.
   * 2.1 One of the altitude lanes is reserved.
   * 2.2 UAVs are divided into take-off groups
   * 2.3 Steps 1-3 are repeated for each group of UAVs with the constraint that the reserved altitude band is not used.
   * 2.4 When a UAV reaches the latitute and longitude of its targeted starting waypoings it descends to the reserved altitude and awaits further instructions.
   * 2.5 Once all groups have been processed and all UAVs are positioned at the reserved altitude at their longitude and latitude, Step 4 is executed.
   
3. One or more UAVs fail to take-off
   * 3.1 Any UAVs that fail to takeoff are ignored during all subsequent synchronizations.
   
4. One UAV flies outside its designated flightpath during synchronized takeoff
   * 4.1 The monitoring system detects the violation and raises an alarm
   * 4.2 DroneResponse issues a hover-in-place command to the rogue UAV
   * 4.3 All UAVs activate high-alert collision avoidance tactics
   * 4.4 The RPIC decides whether to abort the entire mission by sending a global hover_in_place command
   * 4.5 If the mission is aborted, the RPIC issue RTL commands or manually assumes control over each UAV one-by-one.
   
5. In steps 1-4 only one UAV is involved in the synchronized takeoff.
   * 5.1 The UAV is assigned the takeoff altitude of its first target waypoint.
   * 5.2 No synchronization is required with other UAVs.

[Return to use case list](../../README.md)
