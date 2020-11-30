(Needs fixing still)

## Use Case: Air Sampling

**Description**

Multiple UAVs dispatched for air sampling to record air quality

**Primary Actor**

Drone Commander

**Supporting Actors**

Semi-autonomous UAV

**Stakeholders and Interests**

Fire department engaged in environment analysis
 FAA concerned with flight regulations
 General public

**Pre-Conditions**

- Dronology system is active
- Multiple UAVs are equipped with sampling equipment and are placed on the ground and are activated
- Firefighters have marked area of river to be sampled
- DroneResponse is running and all available UAVs are displayed on map
- Monitoring system is tracking the location and status of each available UAV.
- All UAVs are equipped with collision avoidance technology

**Post Conditions**

Success end condition

UAVs successfully reach the targeted area, and return the sampled air-quality record.
Failure end condition:
 UAVs fail to reach the targeted area, or fail to return the sampled air-quality record.

**Trigger**

The Drone Commander activates the sampling mission .

## Main Success Scenario

1. Emergency responders**initiate\_area\_search [SPLC-1001]**
2. The DroneResponse commander issues a command to start the mission.
3. DroneResponse **plans\_route [SPLC-1010]** for the drones to reach the targeted search area.
4. The UAVs **synchronized Takeoff [SPLC-1003]**.
5. The drones head to the location of the marked area.
6. After arriving at its targeted location, UAV switches to &quot;sampling\_mode&quot;. **Perform Analyzing [SPLC-1006]**
7. After finishing its sampling mode, UAVs head to their next specific targeted area (if there is any).
8. Repeats step 6 to 9 until water sampling for all the designated locations is completed.
9. The Drone Commander **ends\_mission [SPLC-1008]**.

## Specific Exceptions

1. In step 3, one of the UAVs fails to takeoff.

   * 1.1 When an alternate UAV is prepped for flight, that UAV is dispatched in place of the failed UAV.

   * 1.2 When no alternate UAV is prepped for flight:

      * 1.2.1 The search\_route\_planner is notified that only a subset of UAVs have been dispatched.

      * 1.2.2 The search\_route\_planner executes [**$**** adjusts route plans$]** for currently available UAVs in flight.

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

1. [https://www.researchgate.net/publication/332429593\_Aerial\_drone\_as\_a\_carrier\_for\_miniaturized\_air\_sampling\_systems](https://www.researchgate.net/publication/332429593_Aerial_drone_as_a_carrier_for_miniaturized_air_sampling_systems)

2.[https://www.researchgate.net/publication/282045680\_Development\_of\_a\_multicopter-carried\_whole\_air\_sampling\_apparatus\_and\_its\_applications\_in\_environmental\_studies](https://www.researchgate.net/publication/282045680_Development_of_a_multicopter-carried_whole_air_sampling_apparatus_and_its_applications_in_environmental_studies)
