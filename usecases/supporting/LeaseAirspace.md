## Use Case: Lease Airspace for Planned Flight Path

**ID**

SC10

**Description**

All UAVs must receive airspace authorization prior to commencing flight to a waypoint. Collisions are prevented through a multi-faceted approach of collision avoidance for unplanned violations of minimum separation distance, and just-in-time airspace reservations from the UAVs current coordinates to a target coordinate.

**Invoked by**


| [River and Ice Rescue](../main/RiverRescue.md) | [Item Delivery](../main/ItemDelivery.md)| [AccidentSurveillance](../main/AccidentSurveillance.md) | [StructuralFire](../main/StructuralFire.md) | [EnvironmentalSampling](../main/EnvironmentalSampling.md) |
| :------: | :--------: | :--------: | :------: |:------: |
|  x | x  | x  | x  |x  |
|  Also indirectly from [Synchronized Takeoff](SynchronizedTakeoff.md)<br>[End Mission](EndMission.md) | Only indirectly from [Synchronized Takeoff](SynchronizedTakeoff.md)<br>[Fly To Destination](FlyToDestination.md) | Also indirectly from [Synchronized Takeoff](SynchronizedTakeoff.md)<br>[End Mission](EndMission.md) |Also indirectly from [Synchronized Takeoff](SynchronizedTakeoff.md)<br>[End Mission](EndMission.md)|Also indirectly from [Synchronized Takeoff](SynchronizedTakeoff.md)<br>[End Mission](EndMission.md) |

**Primary Actor**

- Semi-Autonomous UAV

**Supporting Actors**

- Air Traffic Control

**Stakeholders and Interests**

- RPIC
- General public

**Pre-Conditions**

- UAV is either armed and ready-to-fly or already in the air

**Post Conditions**

_Success end condition:_

- UAVs always receive permission from ATC before commencing flight to a waypoint.

_Failure end condition:_

- UAVs fly to a waypoint without authorization creating the potential for a mid-air collision.

**Trigger**

The UAV needs to fly to a waypoint or needs some space to perform an action.

## Main Success Scenario

1. The UAV calculates the airspace needed for its next action.
2. The UAV requests permission from ATC to reserve the airspace identified.
3. ATC determines that the airspace can be reserved.
4. ATC reserves the airspace.
5. ATC releases any airspace reservations previously held by the UAV.
6. ATC grants the UAV an exclusive lease of the airspace.
7. The UAV completes its action and goes to step 1.

## Exceptions

1. All ubiquitous exceptions are handled.

2. In step 3, ATC determines that the airspace is not currently available.
   * 2.1 ATC finds all reservations held by other UAVs that share some altitude with the requested airspace.
   * 2.2 ATC finds all restricted airspace that shares some altitude and is less than 1000 meters from the requested airspace.
   * 2.3 ATC denies the request for airspace and attaches both the list of other reservations and the list of restricted airspaces.
   * 2.4 The UAV analyzes the attached lists and selects an alternative action among:
      * 2.4.0 If the action is impossible because of restricted airspace
         * 2.4.0.1 TBD
      * 2.4.1 If the next action is to fly to a waypoint, and the UAV determines that meaningful progress is possible then
         * 2.3.1.1 The UAV picks a new waypoint that moves it closer to the target.
         * 2.3.1.2 The use case continues at step 1.
      * 2.4.2 If progress on the next action is possible, then
         * 2.3.2.1 The UAV decides on a new next action.
         * 2.3.2.2 The use case continues at step 1.
      * 2.4.3 If progress is not possible, and the UAV is in the air, then
         * 2.4.3.1 The UAV requests a small amount of airspace to wait within. This new airspace must fit inside the airspace that the UAV has already reserved. The UAV is guaranteed to get a lease on the new airspace in case it fits within its current airspace.
         * 2.4.3.2 The UAV waits for a random time interval (< 5 seconds) and repeats its request for airspace.
         * 2.4.3.3 The use case continues at step 3.
      * 2.4.4 If the UAV is on the ground, awaiting takeoff, and progress is not possible, then
         * 2.4.4.1 The UAV waits for a random time interval (< 5 seconds) and repeats its request for airspace.
         * 2.4.4.2 The use case continues at step 3.

[Return to use case list](../../README.md)
