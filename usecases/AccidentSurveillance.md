**Use Case:** Provide surveillance and information about a traffic accident

**ID** : SPCL-13

**Description**

One or more UAVs are dispatched to a traffic accident scene in order to provide information to the emergency responders.

**Primary Actor**

UAV&#39;s

**Supporting Actors**

Firefighters, Police, Medical crews

**Stakeholders and Interests**

Having specific information about a car accident (how many cars are involved, what is the exact location, traffic jams, people injured, etc) can help emergency responders having the proper reactions.

**Pre-Conditions**

- Dronology system is active
- Multiple UAVs are equipped with cameras and are placed on the ground and are activated
- DroneResponse received a approximative target position
- Search plan has been generated
- DroneResponse is running and UAVs are displayed on map
- An accident really is confirmed to be near the approximative target position
- All UAVs are equipped with collision avoidance technology

**Post Conditions**

Success end condition

The accident has been precisely located and relevant information has been transmitted to emergency responders.
Failure end condition:
 The accident has not been found (&quot;Prank ?&quot;).

**Trigger**

A 911 call operator receives a call reporting an accident

## **Main Success Scenario**

1. A 911 call happens, the operator asks for the location, evaluates the situation and assigns a specific number of drones for the mission.
2. Emergency responders **initiate\_area\_search [SPLC-1001]**
3. DroneResponse **plans\_route [SPLC-1010]**for the drones to reach the targeted search area.
4. The DroneResponse commander issues a command to start the mission.
5. The UAVs **synchronized Takeoff [SPLC-1003]**.
6. The drones fly to the location of the accident.
7. The UAVs reach the target area and **perform\_search [SPLC-1002]**.
8. Once one of the UAVs detects the exact accident location.
9. The UAV sends the imagery and GPS coordinates to the human operator and **requests for permission[SPLC-1009]** to double check on the target/accident.
10. The UAV receives confirmation from the human operator that the accident detection is valid.
11. DroneResponse sends accident coordinates to other UAV&#39;s participating in the mission.
12. The UAVs switch to &quot;information\_gathering&quot; mode and send specific information ( i.e number of cars, presence of fire, victims on the ground, toxic material leakage) along with imagery to DroneResponse.
13. The precise GPS coordinate of the accident and the surroundings of the road are sent to the emergency responders.
14. Specific information gathered by UAV&#39;s is processed and classified into specific emergency categories and are sent to related emergency services. (Traffic information sent to the police, accident structure information sent to the firefighters, human related information sent to medical staff)..
15. The Drone Commander **ends\_mission** **[SPLC-1008]**.

## **Specific Exceptions:**

1. No drone can locate the accident.
   * 1.1 An alert is sent through DroneResponse claiming that the accident can&#39;t be located
   * 1.2 DroneResponse displays images from the camera of each drones
   * 1.3 The Drone Commander checks for the images and marks the accident as soon as it locates the accident on one drone&#39;s camera.

2. In step 8, the UAV detects a possible accident site at a confidence level below victim\_detected threshold but above the lowest `ignore&#39; level.
   * 2.1 The UAV logs the alert including saved imagery
   * 2.2 DroneResponse saves the GPS coordinates of the sighting
   * 2.3 The UAV continues its currently assigned route.
   * 2.4 The back-up operator reviews the streamed imagery
   * 2.5 The back-up operator confirms that the sighting is not a victim.


## **General Exceptions:**

1. In step 5, one of the UAVs fails to takeoff.
   * 2.1 When an alternate UAV is prepped for flight, that UAV is dispatched in place of the failed UAV.
   * 2.2 When no alternate UAV is prepped for flight:
   * 2.3 The search\_route\_planner is notified that only a subset of UAVs have been dispatched.
   * 2.4 The search\_route\_planner executes [**$**** adjusts route plans$]** for currently available UAVs in flight.

2. **At any time** , communication is lost between the Ground Control Station and a UAV.

   * See **Lost Drone-to-GCS Communication** (SPLC-2001)

3. At any time, a malfunction error is raised by a UAV in flight.
   *See **Drone-in-flight Malfunction Alert** (SPLC-XXXX)

## **Resources Used:**

[https://www.researchgate.net/publication/313693086\_Using\_drones\_for\_automatic\_monitoring\_of\_vehicular\_accident](https://www.researchgate.net/publication/313693086_Using_drones_for_automatic_monitoring_of_vehicular_accident)

[https://www.ncbi.nlm.nih.gov/pubmed/32183069](https://www.ncbi.nlm.nih.gov/pubmed/32183069)