## Use Case: Environmental Sampling and Analysis

**ID**

UC5

**Description**

UAVs collect and analyze water samples from an open body of water

**Primary Actor**

- Environmental Scientist

-  RPIC

**Supporting Actors**



**Stakeholders and Interests**

- Environmentalists
- Farmers
- General public

**Pre-Conditions**

- DroneResponse is running
- Multiple UAVs are equipped with water sampling mechanisms (and onboard analytics capabilities if required)

**Post Conditions**

_Success end condition:_

The samples are collected successfully from the targeted coordinates

_Failure end condition:_

UAVs fail to collect and/or analyze water samples

**Trigger**

The UAV operator activates the water sampling mission

## Main Success Scenario

1. UAVs are [activated and armed](../supporting/ActivateAndArm.md)
2. Operators [dynamically generate flight routes including sample collection points for the targeted area](../supporting/AreaFlightRouteCoverage.md)
3. DroneResponse requests and receives [flight authorization](../supporting/FlightAuthorization.md)
3. The operator issues a command to start the mission.
4. UAVs [perform synchronized takeoff](../supporting/SynchronizedTakeoff.md)
5. The UAVs fly their assigned routes and [collect and analyze samples](../supporting/CollectAndAnalyseSample.md) at their assigned collection points.
6. When a UAV has completed its collection assignment it returns home.
7. The operator removes samples and replaces and/or replenishes onboard sampling supplies.
8. Steps 4-7 are completed until all needed samples have been collected.
9. The Drone Commander [ends mission](../supporting/EndMission.md).

## Exceptions

1. All [general exceptions](../../README.md#GeneralExceptions) apply

## Resources Used

1. [https://www.sciencedirect.com/science/article/pii/S0048969719312446](https://www.sciencedirect.com/science/article/pii/S0048969719312446)
2. [https://onlinelibrary.wiley.com/doi/abs/10.1002/rob.21591](https://onlinelibrary.wiley.com/doi/abs/10.1002/rob.21591)

<br><br>
[Return to use case list](../../README.md) 
