**DroneResponse Use Cases**

**Use Case:** Active Tracking

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

Either the UAV has raised a victim\_alert or is assuming the currently assigned tracking task of another UAV.

## Main Success Scenario

1. The UAV positions itself in tracking\_position i.e., in the near vicinity of the victim but not directly overhead.
2. The UAV uses onboard image detection to continually mark the victim in the image stream.
3. The UAV&#39;s onboard computer continually calculates the GPS coordinates of the victim and the victim&#39;s direction and distance from the UAV.
4. The UAV&#39;s onboard computer continually calculates the desired position of the UAV to maintain a tracking\_position.
5. The UAV&#39;s onboard computer continually adjusts the position of the UAV in order to maintain the tracking position.
6. Steps 2-5 are repeated until the UAV receives a stop\_tracking command.

## Exceptions

1. **At any time** , communication is lost between the Ground Control Station and a UAV.
   *See **Lost Drone-to-GCS Communication** (SPLC-EX-001)

1. At any time, a malfunction error is raised by a UAV in flight.
   * See **Drone-in-flight Malfunction Alert** (SPC-EX-XXXX)

2. At any time, the UAV scans its surroundings for obstacles to avoid. See **Collision\_Avoidance (SPLC-EX-XXXX)**