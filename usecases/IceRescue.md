**DroneResponse Use Cases**

**Use Case:** Ice Search and Rescue

**ID** : SPLC-11

**Description**

UAV(s) dispatched with a flotation device to rescue person who has fallen through the ice

**Primary Actor**

Drone Commander

**Supporting Actors**

Semi-autonomous UAV

**Stakeholders and Interests**

Fire department engaged in river rescue
 FAA concerned with flight regulations
 General public

**Pre-Conditions**

- Dronology system is active
- UAV is equipped with camera and flotation device
- Emergency responders have marked area of lake in which victim is located
- Ice is brittle making it difficult to reach the person

**Post Conditions**

Success end condition

The UAV successfully delivers a flotation device to the victim.

Failure end condition:
 The victim is not found or the flotation device is delivered out of the victim&#39;s reach.

**Trigger**

The Drone Commander activates the delivery.

## Main Success Scenario

1. Emergency responders [initiate area search](supporting/InitiateAreaSearch.md)
2. The DroneResponse commander issues a command to start the mission.
3. The UAV(s) **synchronized Takeoff [SPLC-1003].**
4. The UAVs **perform\_search** **[SPLC-1002]**
5. The UAV **victim\_confirmation** **[SPLC-1005]** from the human operator.
6. The UAV receives confirmation from the human operator that the victim sighting is valid.
7. DroneResponse automatically sends the GPS coordinates to the mobile\_rescue system.
8. The UAV switches to flotation **device\_delivery** **[SPLC-1011]** mode.
9. Human responders reach the victim's location and execute a rescue.
10. The Drone Commander **ends\_mission**** [SPLC-1008]**.

## Specific Exceptions
1. In step 3, one of the UAVs fails to take-off.
   * 1.1 If a replacement UAV is flight-ready, it is dispatched in place of the failed UAV.
   * 1.2 If no replacement is available DroneResponse re-executes **initiate\_area\_search** [SPLC-1001] for the available UAVs and previously defined search area.

2. In step 4, the UAV detects a possible victim at a confidence level below _candidate\_victim\_detected_ threshold but above the lowest `ignore&#39; level.
   * 2.1 The UAV logs the alert including saved imagery
   * 2.2 DroneResponse saves the GPS coordinates of the sighting
   * 2.3 The UAV continues its currently assigned route.
   * 2.4 The back-up operator reviews the streamed imagery
   * 2.5 The back-up operator confirms that the sighting is not a victim.

3. In step 8, a communication failure occurs between DroneResponse and the Rescuers mobile device. (Now what?)
tbd

## General Exceptions

1. **At any time** , if communication is lost between the Ground Control Station and a UAV, DroneResponse executes the **Lost Drone-to-GCS Communication** (SPLC-2001) exception case.
2. At any time, a malfunction error is raised by a UAV in flight, DroneResponse executes the **Drone-in-flight Malfunction** (SPLC-2002) exception case.

3. In step 5, the UAV detects a possible victim at a confidence level below victim\_detected threshold but above the lowest `ignore&#39; level.
   * 3.1 The UAV logs the alert including saved imagery
   * 3.2 DroneResponse saves the GPS coordinates of the sighting
   * 3.3 The UAV continues its currently assigned route.
   * 3.4 The back-up operator reviews the streamed imagery
   * 3.5 The back-up operator confirms that the sighting is not a victim.

4. In step 8, a communication failure occurs between DroneResponse and the Rescuers mobile device. (Now what?)

**Resources Used:**
(Coming soon)
