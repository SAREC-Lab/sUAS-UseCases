## Use Case: Perform Search

**Description**

UAV performs its predefined search

**Invoked by**


**Primary Actor**

Semi-Autonomous UAV

**Supporting Actors**

Mission Commander

**Stakeholders and Interests**

**Pre-Conditions**

- Each UAV has been assigned a search mission defined by as series of waypoints
- Each UAV is at its own starting waypoint of the designated search.

**Post Conditions**

Success end condition

UAVs search the designated area and if a target is along the route, the target is found.

Failure end condition:

UAV fails to execute the designated search.

**Trigger**

The UAV reaches the GPS coordinates of the first waypoint in a designated search

## Main Success Scenario

1. The UAV activates its camera (if not already activated).
2. The UAV commences to fly its designated routes at the specified velocity.
3. The UAV streams imagery to its onboard companion computer and to DroneResponse.
4. Each UAV's onboard compute processes imagery from its camera using a trained vision model [$VISION\_MODEL$]
5. When a UAV flies within vision range of a victim, its onboard image recognition software detects the victim.
6. When image recognition is greater than the [$image\_recognition\_threshold$], the UAV raises a victim\_alert.

## Exceptions

1. All [general exceptions](../../README.md#GeneralExceptions) apply

3. In step 6, the UAV detects a possible target at a confidence level below [$image\_recognition\_threshold$] but above the lowest ignore level, logs the event, and raises an alert.
