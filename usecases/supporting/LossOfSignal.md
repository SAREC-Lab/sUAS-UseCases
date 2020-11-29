## Exception Case: Loss of Signal

**Description**

Without an onboard pilot, there is a significant reliance on the command and control link, and a greater emphasis on the loss of functionality associated with lost of signal.
This exception case occurs when such a loss of signal occurs.  Most UAVs have some degree of onboard autonomy - varying between the ability to continue flight to the currently assigned
waypoint, execute failsafe mechanisms, and/or complete an entire mission autonomously.

**Primary Actor**

Ground Control System
RPIC
Unmanned Aerial Vehicle

**Supporting Actors**

Air Traffic Control

**Stakeholders and Interests**

- RPIC
- General public

**Pre-Conditions**

- The UAV is in the air and has a command and control link to one or more ground control stations

**Post Conditions**

Success end condition

Either:
- Signal is re-established and the flight continues
- The UAV is landed safely and quickly despite loss of link
- The UAV completes its mission as planned despite loss of signal (Note: This is currently not authorized by FAA)

Failure end condition:

- The UAV is lost and/or crashes.

**Trigger**

The UAV is in flight and loss-of-signal occurs for greater than [loss_of_signal_threshold_seconds].

## Main Exception Scenario

1. The runtime monitoring system detects a loss of signal event for a UAV
2. The runtime monitoring system raises an alert
3. The UI displays the alert in order to notify the RPIC of the loss-of-signal event
4. The operator makes a decision to assume 

DroneResponse decomposes the entire flight path into a series of flight_legs, each one with its own target waypoint.
2. DroneResponse establishes an initial altitude of the flight [starting_altitude] and assigns it as the starting altitude of each individual leg.
3. DroneResponse checks the starting flight_leg to ensure that it does not pass through any prohibited airspace whilst maintaining its [starting_altitude].
4. DroneResponse a terrain map to check the altitude of the flight_leg's terrain to ensure that the UAV maintains [minimum_terrain_separation] whilst maintaining the [starting_altitude] of the current leg.
5. Steps 3-4 are repeated for each flight_leg. 
6. Given the flight plan, the UAV checks that it has sufficient battery power to reach its destination.  It determines that it has sufficient power to continue.
7. The UAV ascends or descends to the target altitude of the current flight leg.
8. The UAV flies to the destination waypoint of the current flight leg.
9. The UAV reports its arrival at the flight leg's destination waypoint.
10. Steps 6-8 are repeated until the UAV reaches its final destination.
11. The use cases finishes when the UAV assumes the task assigned for it to do at its final destination.

## Exceptions

1. All ubiquitous exceptions are handled.

2. In step 6, the UAV determines that it lacks sufficient battery power to complete the mission.
   * 2.1 The UAV notifies the human operator and awaits further instructions.

3. In steps 2 or 3 it is determined that the UAV will pass through prohibited airspace.
   * 3.1 An alternate flight path is planned around the prohibited airspace and/or at a new altitude
   * 3.2 If necessary, the flight path is divided into a series of waypoints representing multiple flight_legs
   * 3.3 Steps 2 and 3 are repeated until a viable flight path is found.
      * 3.3.1 If no viable flight path can be found the operator is notified and the flight is cancelled.
	  * 3.3.1 If a viable flight path is found, then original series of flight_legs is updated with the modified legs

4. In step 6, has been assigned a task that requires additional battery power (e.g., return to home coordinates, survey the landscape). 
   * 4.1 The UAV estimates power requirements for completing the entire task.
   * 4.2 If a return home is required, the UAV estimates power requirements for returning home.
   * 4.3 The UAV estimates total battery requirements required and determines whether it can complete the entire mission.
      * 4.3.1 The UAV determines that it has sufficient power to complete the entire mission and the use case continues with steps 7-11.
	  * 4.3.2 The UAV determines that it lacks sufficient power to complete the entire mission and Exception Use-Case #2 is executed.

   