**Use Case:** Deliver defibrillator to a specific location

**ID** : SPLC-12

**Description**

UAV(s) are dispatched to deliver defibrillators to cardiac patients in a quick time in emergency situations.

**Primary Actor**

Receivers/UAV

**Supporting Actors**

Medic crew

**Stakeholders and Interests**

Medical professions engaged in first rescue materials

**Pre-Conditions**

- Dronology system is active
- Multiple UAVs are equipped with cameras and are placed on the ground and are activated
- Drones are able to carry limited weight
- There are enough drones to take care of the delivery process
- DroneResponse is running and UAVs are displayed on map
- All UAVs are equipped with collision avoidance technology

**Post Conditions**

Success end condition

The medical package has been successfully collected by the target.

Failure end condition:
 The medical package has not been collected by the target.

**Trigger**

The Drone Commander activates the delivery.

Or, A patient requested for emergency defibrillator delivery

## **Main Success Scenario**

1. A user calls 911 to report a medical emergency.
2. The operator identifies the location and uses Google maps to identify GPS coordinates for the delivery.
3. A ready-to-fly UAVwith a pre-attached defibrillator downloads current NOTAMs and**plans\_route [SPLC-1010]** to the patient&#39;s location.
4. Dronology notifies the medic crews and sends them the GPS coordinates of the patient&#39;s location.
5. The UAV(s) **synchronized Takeoff [SPLC-1003]**
6. The delivery drone navigates the terrain autonomously, changing altitude to avoid hills etc.
7. The delivery drone arrives at the specified location.
8. Drones turn on their on-board cameras
9. The delivery drone uses **[$VISION\_MODEL$]** to identify a place to drop the package.
10. The drone **Request\_for\_permission[SPCL-1009]** to\_drop\_package from the operator.
11. The UAV receives confirmation from the human operator to drop the package.
12. The UAVdrops the package.
13. The receivers collect the needed package.
14. The Drone Commander **ends\_mission [SPLC-1008].**

**Specific Exceptions**** :**

1. In step 2, coordinate identification using Google maps is failed
   * 1.1 Another mapping software is used to identify exact coordinates from the address
2. In step 5, the UAV fails to take off
   * 2.1 DroneResponse assigns the current drone configuration to a new drone that has a pre-attached defibrillator
  *  2.2 The new drone takes off to replace the one that failed
3. For some reason, the delivery location has changed.
  * 3.1 DroneResponse identify the coordinates of the new location using Google maps
  * 3.2 DroneResponse transmits the new coordinates to the Drone
  * 3.3 The drone adapts its route and flies toward the new location
4. The Drone Commander denies permission for the drop because the spot is not safe
  * 4.1 The Drone Commander uses the images from the drone camera displayed on DroneResponse to mark a safe spot for the drop on the map
  * 4.2 DroneResponse identify the coordinates for the spot marked on the map
  * 4.3 DroneResponse transmits the new coordinates to the drone
  * 4.4 The drones reaches the new location and drops the package

## **General Exceptions:**

1. **At any time** , communication is lost between the Ground Control Station and a UAV.
*  See **Lost Drone-to-GCS Communication** (SPLC-2001)

2. At any time, a malfunction error is raised by a UAV in flight.
   * See **Drone-in-flight Malfunction Alert** (SPLC-XXXX)

**Resources Used: (just links for now, not final)**

**1.** [**https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5815004/**](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5815004/)

**2.** [**https://www.semanticscholar.org/paper/Use-of-Drone-Technology-for-Delivery-of-Medical-Mesar-Lessig/00f87bee4f44e8985486801f1ef124e3da31d444**](https://www.semanticscholar.org/paper/Use-of-Drone-Technology-for-Delivery-of-Medical-Mesar-Lessig/00f87bee4f44e8985486801f1ef124e3da31d444)