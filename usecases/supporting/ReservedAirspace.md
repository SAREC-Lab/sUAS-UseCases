## Use Case: Reserved Airspace for Planned Flight Path

**Description**

All UAVs must receive airspace authorization prior to commencing flight to a waypoint. Collisions are prevented through a multi-faceted approach of collision avoidance for unplanned violations of minimum separation distance, and just-in-time airspace reservations from the UAVs current coordinates to a target coordinate.

**Primary Actor**

Semi-Autonomous UAV

**Supporting Actors**

Air Traffic Control

**Stakeholders and Interests**

- RPIC
- General public

**Pre-Conditions**

- UAV is either armed and ready-to-fly or already in the air

**Post Conditions**

Success end condition

- UAVs always receive permission from ATC before commencing flight to a waypoint.

Failure end condition:

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

2. (Note: If we support this then we must check for and break deadlocks) In step 3, ATC determines that the airspace is not currently available and notifies the UAV.  
   * 2.1 The UAV requests notification from ATC as soon as the airspace becomes available.
   * 2.2 The UAV hovers in place awaiting notification.
   * 2.3 The airspace becomes available.
   * 2.4 The use case continues with steps 4 to 7.
   
3. (Alternately instead of #2) In step 3, ATC determines that the airspace is not currently available.
   * 3.1 ATC denies the request for airspace.
   * 3.2 The UAV waits for a random time interval (< 5 seconds) and repeats its request for airspace.
   * 3.3 The UAV repeats step 3.2 until it receives airspace authorization at which point the use case continues with steps 4-7.

4. (Alternatively instead of #2 or #3) In step 3, ATC determines that the airspace is not currently available.
   * 4.1 ATC finds all reservations held by other UAVs that share some altitude with the requested airspace.
   * 4.2 ATC finds all restricted airspace that shares some altitude and is less than 1000 meters from the requested airspace.
   * 4.2 ATC denies the request for airspace and attaches both the list of other reservations and the list of restricted airspaces.
   * 4.3 The UAV analyzes the attached lists and selects an alternative action among:
      * 4.3.0 If the action is impossible because of restricted airspace
         * 4.3.0.1 TBD
      * 4.3.1 If the next action is to fly to a waypoint, and the UAV determines that meaningful progress is possible then
         * 4.3.1.1 The UAV picks a new waypoint that moves it closer to the target.
         * 4.3.1.2 The use case continues at step 1.
      * 4.3.2 If progress on the next action is possible, then
         * 4.3.2.1 The UAV decides on a new next action.
         * 4.3.2.2 The use case continues at step 1.
      * 4.3.3 If progress is not possible, and the UAV is in the air, then
         * 4.3.3.1 The UAV requests a small amount of airspace to wait within. This new airspace must fit inside the airspace that the UAV has already reserved. The UAV is guaranteed to get a lease on the new airspace in case it fits within its current airspace.
         * 4.3.3.2 The UAV waits for a random time interval (< 5 seconds) and repeats its request for airspace.
         * 4.3.3.3 The use case continues at step 3.
      * 4.3.4 If the UAV is on the ground, awaiting takeoff, and progress is not possible, then
         * 4.3.4.1 The UAV waits for a random time interval (< 5 seconds) and repeats its request for airspace.
         * 4.3.4.2 The use case continues at step 3.

   
