**DroneResponse Use Cases**

**Use Case:** Structural fire fighting

**ID** : SPLC-14

**Description**

Multiple UAVs dispatched to analyze the structure for fire fighting

**Primary Actor**

Drone Commander

**Supporting Actors**

Semi-autonomous UAV

**Stakeholders and Interests**

Fire department engaged in fire fighting
 FAA concerned with flight regulations
 General public

**Pre-Conditions**

- Dronology system is active
- Multiple UAVs are equipped with normal/thermal cameras and are placed on the grund and are activated
- Firefighters have marked the building to be analyzed
- DroneResponse is running and all available UAVs are displayed on map
- Monitoring system is tracking the location and status of each available UAV.
- A building is in the search area
- All UAVs are equipped with collision avoidance technology

**Post Conditions**

Success end condition

The building is analyzed with fire situations by a UAV, and info is sent back to firefighters.
Failure end condition:
 The building cannot be analyzed or the info is not sent back to firefighters successfully.

**Trigger**

The Drone Commander activates the search.

## Main Success Scenario

1. Emergency responders**initiate\_area\_search [SPLC-1001]**
2. The DroneResponse commander issues a command to start the mission.
3. The UAVs **synchronized Takeoff [SPLC-1003]**.
4. After reaching the marked building, the UAVs switch to &quot;analyzing mode&quot; and **Perform Analyzing[SPLC-1006]**
5. When the building is finished analyzed, the drone sends back the structure info related to the fire fighting, such as heatmap and damage situation of the specific area. Human responders assign their fire-fighting/rescue routes based on the sent-back info.
6. The Drone Commander **ends\_mission** **[SPLC-1008]**.

## Specific Exceptions

1. In step 3, one of the UAVs fails to takeoff.

   * 1.1 When an alternate UAV is prepped for flight, that UAV is dispatched in place of the failed UAV.

   * 1.2 When no alternate UAV is prepped for flight:

   * 1.3 The search\_route\_planner is notified that only a subset of UAVs have been dispatched.

   * 1.4 The search\_route\_planner executes [**$**** adjusts route plans$]** for currently available UAVs in flight.

## General Exceptions

1. **At any time** , communication is lost between the Ground Control Station and a UAV.

   * See **Lost Drone-to-GCS Communication** (SPLC-2001)

1. At any time, a malfunction error is raised by a UAV in flight.
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

1. [https://www.semanticscholar.org/paper/Unmanned-Aerial-Systems-in-the-Fire-Service%3A-and-Griffith-Wakeham/a34e38307a88fda699da7d1aa6d64231ff717d55](https://www.semanticscholar.org/paper/Unmanned-Aerial-Systems-in-the-Fire-Service%3A-and-Griffith-Wakeham/a34e38307a88fda699da7d1aa6d64231ff717d55)
2.