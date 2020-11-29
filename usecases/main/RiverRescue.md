## Use Case: River Search and Rescue

**Description**

Multiple UAVs dispatched to search for victim in river

**Primary Actor**

Drone Commander

**Supporting Actors**

Semi-autonomous UAV

**Stakeholders and Interests**

- Fire department engaged in river rescue
- FAA concerned with flight regulations
- General public

**Pre-Conditions**

- DroneResponse is running
- Multiple UAVs are equipped with cameras
- A victim is in the river

**Post Conditions**

Success end condition

The victim is found by a UAV and actively tracked until a first responder takes over the rescue operation
Failure end condition:
 The victim is not found or the victim is found but not actively tracked.

**Trigger**

The Drone Commander activates the search.

## Main Success Scenario

1. UAVs are [activated and armed](../supporting/ActivatedAndArmed.md)
2. Emergency responders [initiate area search](../supporting/InitiateAreaSearch.md)
3. The DroneResponse commander issues a command to start the mission.
4. The UAVs [perform synchronized takeoff](../supporting/SynchronizedTakeoff.md)
5. The UAVs [perform area search](../supporting/PerformAreaSearch.md)
6. When a potential victim is detected by a UAV, that UAV immediately switches to [active tracking](../supporting/ActiveTracking.md) mode.
7. The UAV requests [victim confirmation](supporting/VictimConfirmation.md) from the human operator.
8. The UAV receives confirmation from the human operator that the victim sighting is valid.
9. DroneResponse automatically sends the GPS coordinates to the mobile_rescue system.
10. Human responders arrive at the scene.
11. The Drone Commander [ends mission](supporting/EndMission.md).

## Specific Exceptions
(Move to arming case)

1. In step 3, one of the UAVs fails to takeoff.

   * 1.1 When an alternate UAV is prepped for flight, that UAV is dispatched in place of the failed UAV.

   * 1.2 When no alternate UAV is prepped for flight:

      * 1.2.1 The search\_route\_planner is notified that only a subset of UAVs have been dispatched.

      * 1.2.2 The search\_route\_planner executes [initiate area search](../supporting/InitiateAreaSearch.md) for currently available UAVs in flight.

## General Exceptions

1. **At any time** , communication is lost between the Ground Control Station and a UAV.

   * See **Lost Drone-to-GCS Communication** (SPLC-2001)

2. At any time, a malfunction error is raised by a UAV in flight.

   * See **Drone-in-flight Malfunction Alert** (SPLC-XXXX)

3. In step 5, the UAV detects a possible victim at a confidence level below victim\_detected threshold but above the lowest `ignore&#39; level.

   * 3.1 The UAV logs the alert including saved imagery

   * 3.2 DroneResponse saves the GPS coordinates of the sighting

   * 3.3 The UAV continues its currently assigned route.

   * 3.4 The back-up operator reviews the streamed imagery

   * 3.5 The back-up operator confirms that the sighting is not a victim.

4. In step 8, a communication failure occurs between DroneResponse and the Rescuers mobile device. (Now what?)
   * tbd


**Resources Used:**

1. Ankit Agrawal, Sophia Abraham, Benjamin Burger, Chichi Christine, Luke Fraser, John Hoeksema, Sara Hwang, Elizabeth Travnik, Shreya Kumar, Walter Scheirer, Jane Cleland-Huang, Michael Vierhauser, Ryan Bauer, Steve Cox: The Next Generation of Human-Drone Partnerships: Co-Designing an Emergency Response System, CHI 2020.
2. Jane Cleland-Huang, Michael Vierhauser: Discovering, Analyzing, and Managing Safety Stories in Agile Projects. RE 2018: 262-273
