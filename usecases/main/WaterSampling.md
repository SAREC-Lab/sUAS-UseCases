## Use Case: Water Sampling and Analysis

**Description**

UAVs collect and analyze water samples from an open body of water

**Primary Actor**

Environmental Scientist
RPIC

**Supporting Actors**



**Stakeholders and Interests**

Environmentalists, farmers, public

**Pre-Conditions**

- DroneResponse is running
- Multiple UAVs are equipped with water sampling mechanisms (and onboard analytics capabilities if needed)

**Post Conditions**

Success end condition

The samples are collected successfully from the targeted coordinates

Failure end condition:

UAVs fail to collect and/or analyze water samples

**Trigger**

The UAV operator activates the water sampling mission

## Main Success Scenario

1. UAVs are [activated and armed](../supporting/ActivateAndArm.md)
2. Operators [dynamically generate flight routes including sample collection points for the targeted area](../supporting/AreaFlightRouteCoverage.md)
3. DroneResponse requests and receives [flight authorization](../supporting/FlightAuthorization.md)
3. The oeprator issues a command to start the mission.
4. UAVs [perform synchronized takeoff](../supporting/SynchronizedTakeoff.md)
5. The UAVs [perform the search](../supporting/PerformSearch.md)
6. When a potential victim is detected by a UAV at a confidence level about [victim_detected] threshold and raises a [victim_detection] event.
7. DroneResponse forwards the event to all UIs registered to receive victim_detection alerts.
8. The UAV immediately switches to [active tracking](../supporting/ActiveTracking.md) mode.
9. DroneResponse requests [victim confirmation](supporting/VictimConfirmation.md) from the human operator.
10. The UAV receives confirmation from the human operator that the victim sighting is valid.
11. Human responders arrive at the scene with their own flotation devices. They attempt a rescue.
12. The Drone Commander [ends mission](supporting/EndMission.md).


1. Drone commander marks each area to search and **initiate\_area\_search [SPLC-1001]**
2. DroneResponse **plans\_route [SPLC-1010]** for the drones to reach the targeted search area.
3. The UAVs **synchronized Takeoff [SPLC-1003]**.
4. The drones fly to the location of the water sampling sites.

1. After arriving at its targeted location, UAV switches to &quot;sampling\_mode&quot;.
2. After finishing its sampling mode, UAVs head to their next specific targeted water area (if there is any).
3. Repeats step 6 to 9 until water sampling for all the designated locations is completed.
4. The Drone Commander **ends\_mission [SPLC-1008]**.

##


## Specific Exceptions:

1. Drone arrives on scene and there is no water place
   * 1.1 The Drone Commander is alerted through DroneResponse
   * 1.2 The Drone Commander has to define a new place on DroneResponse map
   * 1.3 New coordinates are transmitted to the drone
2. UAV fails to fill the sampling container due to external factors
3. UAV fails to head to next targeted water area due to battery
   *3.1 Remaining areas are assigned to the other flying drones or new drones takeoff if the battery of the flying ones is not sufficient to cover all area

##


## General Exceptions:

1. In step 5, one of the UAVs fails to takeoff.
   * 1.1 When an alternate UAV is prepped for flight, that UAV is dispatched in place of the failed UAV.
   * 1.2 When no alternate UAV is prepped for flight:
      * 1.2.1 The search\_route\_planner is notified that only a subset of UAVs have been dispatched.
      * 1.2.2 The search\_route\_planner executes [**$**** adjusts route plans$]** for currently available UAVs in flight.

2. **At any time** , communication is lost between the Ground Control Station and a UAV.

   * See **Lost Drone-to-GCS Communication** (SPLC-2001)

3. At any time, a malfunction error is raised by a UAV in flight.
   * See **Drone-in-flight Malfunction Alert** (SPLC-XXXX)

Resources Used:

1. [https://www.sciencedirect.com/science/article/pii/S0048969719312446](https://www.sciencedirect.com/science/article/pii/S0048969719312446)
2. [https://onlinelibrary.wiley.com/doi/abs/10.1002/rob.21591](https://onlinelibrary.wiley.com/doi/abs/10.1002/rob.21591)
