## Use Case:  Victim_Confirmation

**Description**

UAV requests and receives victim confirmation or refutation from a human operator

**Invoked by**
[IceRescue](../main/IceRescue.md), [RiverRescue](../main/RiverRescue.md)

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

## Exceptions

1. All [general exceptions](../../README.md#GeneralExceptions) apply.

2. In steps 4 and 5 the user refutes the victim sighting
   * 2.1 The drone commander refutes that the sighting is of a victim.
   * 2.2 Drone Response sends a victim\_NOT\_found message to the UAV.

3. In steps 4 and 5 the user is unable to confirm or refute the sighting.

   * 3.1 The drone commander is uncertain whether the imagery is of a victim and requests additional imagery.
   * 3.2 The UAV autonomously flies around the location of the victim sighting and collects additional imagery.
   * 3.2 The operator either confirms the victim has been found (resume from step 5) or refutes the sighting in which case the UAV continues its previous search plan.

4. In steps 2 and steps 6, no acknowledgement is received from the operator within a specified time period.

   * 4.1 The UAV attempts to resend the alert and to route the alert and associated images through other participating drones.

[Return to use case list](../../README.md)
