## Use Case: River Search and Rescue 

**ID**

UC1

**Description**

Multiple UAVs dispatched to search for victim in river or finding the victim under the ice.

**Primary Actor**

- Drone Commander

**Supporting Actors**

- Semi-autonomous UAV

**Stakeholders and Interests**

- Fire department engaged in river rescue
- FAA concerned with flight regulations
- General public

**Pre-Conditions**

- DroneResponse is running
- Multiple UAVs are equipped with cameras
- A victim is in the river

**Post Conditions**

_Success end condition:_

The victim is found by a UAV and actively tracked until a first responder takes over the rescue operation

_Failure end condition:_

The victim is not found or the victim is found but not actively tracked.

**Trigger**

The Drone Commander activates the search.

## Main Success Scenario

1. UAVs are placed in their launch positions.
2. UAVs are [activated and armed](../supporting/ActivateAndArm.md).
3. Emergency responders initiate the [dynamic generation of flight routes for the targeted area](../supporting/AreaFlightRouteCoverage.md).
4. The DroneResponse commander issues a command to start the mission.
5. The UAVs tasked with search [perform synchronized takeoff](../supporting/SynchronizedTakeoff.md).
6. The UAVs [lease airspace](../supporting/LeaseAirspace.md) and fly their assigned flight routes.
7. While flying their assigned routes, the UAVs perform [image capture and analysis](../supporting/ImageCaptureAndAnalysis.md).
8. When a potential victim is detected by a UAV at a confidence level about `[victim_detected]` threshold a `[victim_detection]` event is raised.
9. DroneResponse forwards the event to all UIs registered to receive victim_detection alerts.
10. The UAV immediately switches to [active tracking](../supporting/ActiveTracking.md) mode.
11. DroneResponse requests [victim confirmation](../supporting/VictimConfirmation.md) from the human operator.
12. The UAV receives confirmation from the human operator that the victim sighting is valid.
13. DroneResponse automatically sends the GPS coordinates to the mobile_rescue system.
14. A UAV tasked with delivering a flotation device  [performs item delivery](ItemDelivery.md)
15. Human responders arrive at the scene.
16. The Drone Commander [ends mission](../supporting/EndMission.md).

## Alternative Steps 

1. In steps 14 and 15, human responders deliver the flotation device manually without the help of the UAV. 

## Exceptions

1. All [general exceptions](../../README.md#GeneralExceptions) apply, except for those with [in_air] preconditions.

2. In step 7, the UAV detects a possible victim at a confidence level below [victim_detected] threshold but above the lowest [ignore_level].
   * 2.1 The UAV raises a notification including saved imagery.
   * 2.2 DroneResponse saves the GPS coordinates of the sighting.
   * 2.3 The UAV continues its currently assigned route.
   * 2.4 The back-up operator reviews the streamed imagery.
   * 2.5 The back-up operator confirms that the sighting is not a victim.

3. In step 11 the human operator refutes the validity of the sighting.
   * 3.1 The UAV resumes its previous search activity in Step 5.
   
4. In step 10, the UAV does not have permission to start automatic tracking when it detects a candidate victim.
   * 4.1 The UAV continues its search as described in step 5 without switching to tracking mode.
   * 4.2 If the human operator confirms the victim sighting, the original UAV immediately attempt to relocate the victim and start tracking.
   
5. At any time after a victim has been detected.
   * 5.1 The human operator reassigns a new UAV to perform the tracking task.
   * 5.2 The current UAV waits to be assigned a new task (e.g., rejoin the search, return home).


## Resources Used

1. Ankit Agrawal, Sophia Abraham, Benjamin Burger, Chichi Christine, Luke Fraser, John Hoeksema, Sara Hwang, Elizabeth Travnik, Shreya Kumar, Walter Scheirer, Jane Cleland-Huang, Michael Vierhauser, Ryan Bauer, Steve Cox: The Next Generation of Human-Drone Partnerships: Co-Designing an Emergency Response System, CHI 2020.
2. Jane Cleland-Huang, Michael Vierhauser: Discovering, Analyzing, and Managing Safety Stories in Agile Projects. RE 2018: 262-273.

[Return to use case list](../../README.md) 
