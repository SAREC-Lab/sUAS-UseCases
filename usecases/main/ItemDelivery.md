## **Use Case:** Deliver medical device to a specific location

**ID** : SPLC-12

**Description**

UAV(s) are dispatched to deliver defibrillators or other medical devices in an emergency situation.

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

1. Medical device delivery is requested due to an emergency situation.
2. The operator uses the map to identify GPS coordinates for the delivery.
3. DroneResponse plans the route and requests [flight authorization](../supporting/FlightAuthorization.md)
4. Flight permissions are confirmed.
4. One or more UAV executes a [synchronized takeoff](../supporting/SynchronizedTakeoff.md)
5. The UAV navigates to the target destination.
6. The UAV [delivers the item](../supporting/ItemDrop.md)
7. The UAV returns home. 

**Specific Exceptions**** :**

- See exceptions in supporting use cases

## **General Exceptions:**

1. All ubiquitous exceptions are handled

**Resources Used:

**1.** [**https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5815004/**](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5815004/)

**2.** [**https://www.semanticscholar.org/paper/Use-of-Drone-Technology-for-Delivery-of-Medical-Mesar-Lessig/00f87bee4f44e8985486801f1ef124e3da31d444**](https://www.semanticscholar.org/paper/Use-of-Drone-Technology-for-Delivery-of-Medical-Mesar-Lessig/00f87bee4f44e8985486801f1ef124e3da31d444)
