**DroneResponse Use Cases**

**Use Case:** Victim_Confirmation

**ID** : SPLC-1005

**Description**

UAV requests and receives victim confirmation or refutation from a human operator

**Invoked by**
[IceRescue.md](../usecases/IceRescue.md)

**Rationale**
The UAV has identified a victim at some degree of confidence and seeks confirmation from a human operator.

**Primary Actor**

Semi-Autonomous UAV

**Supporting Actors**

Human Operator

**Stakeholders and Interests**

**Pre-Conditions**

- UAV has detected a victim with confidence greater or equal to _minimum\_detection\_confidence._

**Post Conditions**

Success end condition

A human operator correctly confirms or refutes the sighting of the victim.

Failure end condition:
 A human operator either fails to respond to the request for confirmation or incorrectly confirms or refutes the sighting of the victim.

**Trigger**

The UAV detects a possible victim using its onboard image detection.

## Main Success Scenario

1. The drone generates a victim\_found alert which is transmitted to DroneResponse.
2. DroneResponse acknowledges receipt of the alert via a message to the UAV
3. DroneResponse raises the victim\_found alert on the UI for inspection by a human operator.
4. The Drone Commander inspects the video stream.
5. The Drone Commander confirms that a victim has been found.
6. DroneResponse sends a victim\_found confirmation message to a UAV.

## Specific Exceptions

1. **In steps 4 and 5 (Victim Refuted)**:

   * 1.1 The drone commander refutes that the sighting is of a victim.
   * 1.2 Drone Response sends a victim\_NOT\_found message to the UAV.
   * 1.3 End scenario.

2. **In steps 4 and 5 (Additional Imagery Requested):**

   * 2.1 The drone commander is uncertain whether the imagery is of a victim and **requests\_additional\_imagery** **[SPLCXXX]**

   * 2.2 The drone commander either confirms the victim has been found (go to Step 5) or refutes the sighting (go to Step 1b)

3. **In step 2 (No acknowledgement received)**:

   * 3.1 The drone does not receive an acknowledgement from DroneResponse with a specified time. It attempts to resend the alert and to route the alert and associated images through other participating drones.

4. **In step 6 (No confirmation received)**:

   * 4.1 After a prespecified time period, the drone does not receive either a confirmation, refutation, or request for additional imagery from the human operator and continues in active tracking mode whilst transmitting updated information.

## General Exceptions

1. **At any time** , communication is lost between the Ground Control Station and a UAV.

   * See **Lost Drone-to-GCS Communication** (SPLC-EX-001)

2. At any time, a malfunction error is raised by a UAV in flight.
   * See **Drone-in-flight Malfunction Alert** (SPC-EX-XXXX)

3. At all times, every UAV in flight scans its surroundings for obstacles to avoid. See **Collision\_Avoidance (SPLC-EX-XXXX)**