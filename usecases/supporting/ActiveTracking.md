## Use Case: Active Tracking

**ID** : SPLC-1004

**Description**

A UAV actively tracks a victim

**Rationale**
During search and rescue, once a victim is detected, the UAV must hover over the victim and track if the victim is moving.

**Primary Actor**

Semi-Autonomous UAV

**Supporting Actors**

Mission Commander

**Stakeholders and Interests**

**Pre-Conditions**

- UAV is within near vision-range of the victim
- UAV has actively tagged the victim

**Post Conditions**

Success end condition

The UAV remains within near vision-range of the victim and streams video imagery to Emergency Responders

Failure end condition:

UAV fails to actively track the victim

**Trigger**

The UAV is assigned or assumed the task of tracking a person

## Main Success Scenario

1. The UAV positions itself in tracking\_position i.e., in the near vicinity of the victim but not directly overhead.
2. The UAV uses [image capture and analysis](ImageCaptureAndAnalysis.md) to continually tag the victim in the image stream.
3. Based on the UAV's position (heading, pitch, roll, yaw) onboard tracker continually calculates the relative position of the victim with respect to the UAV.
4. The onboard tracker generates appropriate velocity vectors to fly towards the victim, without flying directly over the victim and maintaining victim_separation_distance and always flying at an altitude greater than minimum_altitude.
5. The velocity vector is sent to the UAV's autopilot and executed to enable the UAV to track the victim.
6. Steps 2-5 are repeated until the UAV receives a [stop_tracking] command.

## Exceptions

1. All [general exceptions](../../README.md#GeneralExceptions) apply.

2. In step 2, if the UAV loses track of the victim, it attempts to re-tag the victim by changing altitude and performing a localized search.

3. At any time if the onboard vision fails, the UAV raises an alert.

4. If the UAV's battery level goes below a safe level, the UAV raises an alert and requests a replacement UAV to assume the tracking task.

