## Use Case: Safe Passage

**Description**

All UAVs must receive airspace authorization prior to commencing flight to a waypoint. Collisions are prevented through a multi-faceted approach of collision avvoidance for unplanned violations of minimum separation distance, and just-in-time airspace reservations from the UAVs current coordinates to a target coordinate.

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

The UAV needs to fly to a waypoint.

## Main Success Scenario

1. The UAV requests permission from ATC to fly to the waypoint.
2. ATC calculates the airspace needed for the flight.
3. ATC determines that the airspace can be reserved.
4. ATC reserves the airspace for a given time interval.
5. ATC assigns the UAV permission to fly to the waypoint.
6. The UAV arrives at the waypoint and notifies ATC.
7. ATC releases the airspace.

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
   
4. In step 1, the direct path from the UAV's current waypoint to the requested waypoint passes through restricted airspace.
   * tbd (who is responsible for proposing a new route?)
   
