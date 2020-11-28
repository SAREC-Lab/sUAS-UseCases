**DroneResponse Use Cases**

**Use Case:** Collect water samples

**ID** : SLPC-15

**Description**

Multiple UAVs head to a specific area to sample water

**Primary Actor**

Drone Commander

**Supporting Actors**

Semi-autonomous UAV, Incident Commander

**Stakeholders and Interests**

firefighters, chemical researchers

**Pre-Conditions**

- Dronology system is active
- Multiple UAVs are equipped with cameras. Sampling systems are placed on the active drones
- Firefighters/researchers have marked specific area to be sampled of the water quality
- Sample route has been generated
- DroneResponse is running and UAVs are displayed on map
- Each drone is able to carry multiple sampled containers
- All UAVs are equipped with collision avoidance technology

**Post Conditions**

Success end condition

The samples are collected successfully by each UAV with its assigned water area.
Failure end condition:
 Drones fails to collect samples back to home base

**Trigger**

The Drone Commander activates the search.

## Main Success Scenario

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
