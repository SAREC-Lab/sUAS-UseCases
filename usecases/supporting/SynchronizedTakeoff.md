**DroneResponse Use Cases**

**Use Case:** Synchronized Takeoff

**Description**

A cohort of UAVs takeoff and fly to initial waypoints using coordinated flight paths

**Invoked by**
[IceRescue](../main/IceRescue.md), [RiverRescue](../main/RiverRescue.md)

**Rationale**
Synchronized takeoff is needed so that UAVs don&#39;t collide when they take off and potentially cross paths on their way to their initial waypoints.

**Primary Actor**

Semi-Autonomous UAV

**Supporting Actors**

Mission Commander

**Stakeholders and Interests**

**Pre-Conditions**

- Each UAV is on the ground ready to takeoff
- Each UAV has been assigned a starting waypoint.

**Post Conditions**

Success end condition

Each UAV reaches its initial waypoint without collision

Failure end condition:
 Collision occurs at takeoff or during flight to initial waypoints

**Trigger**

The UAVs receive the start mission command.

## Main Success Scenario

1. Dronology assigns each UAV an altitude between 20 feet and the maximum allowed altitude of the current flight area. Each altitude is separated by _minimum\_separation\_distance_ from all other UAVs.
2. Each UAV takes off to its prescribed altitude and waits for all other UAVs to reach their altitudes.
3. Each UAV flies at its unique altitude to the longitude and latitude coordinates of its first waypoints. It waits for confirmation that all other UAVs have reached their designated coordinates.
4. Each UAV then descends or ascends to the designated altitude of its first waypoint and awaits confirmation that all other UAVs have reached their designated altitudes.

## Exceptions
To add -- not enough distinct altitude lanes!

