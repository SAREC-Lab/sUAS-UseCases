**DroneResponse Use Cases**

**Use Case:** End mission

**Description**

Recall UAV(s) back to their home-bases

**Invoked by**

[IceRescue](../main/IceRescue.md), [RiverRescue](../main/RiverRescue.md), [AccidentSurveillance](../main/AccidentSurveillance.md), [AirSampling](../main/AirSampling.md), [WaterSampling](../main/WaterSampling.md), [DefibrillatorDelivery](../main/DefibrillatorDelivery.md), [StructuralFire](../main/StructuralFire.md)

**Primary Actor**

Drone Commander

**Supporting Actors**

Semi-autonomous UAV

**Stakeholders and Interests**

**Pre-Conditions**

- UAVs active and registered with DroneResponse
- DroneResponse is active

**Post Conditions**

Success end condition

- All UAVs safely returned to launch and deactivated

Failure end condition:
- One or more UAV does fails to return to a safe landing base

**Trigger**

- An emergency responder decides to abort the mission
- The mission is complete and an end mission command is initiated

## Main Success Scenario

1. The mission is completed and UAVs are recalled home.
2. The system checks that all recalled UAVs have unique home coordinates.
3. UAVs each plan their own routes back to their unique home coordinates.
4. Each UAV requests airspace clearance for the next leg of its planned route and awaits clearance.
5. When the UAV receives clearance for the next leg of its return flight it flies to the target waypoint.
6. Steps 4-5 are repeated until the UAV returns to its launch coordinates and lands safely.

## Exceptions

1. Step 1 is replaced by an alternate trigger in which the mission commander manually ends the mission and recalls all UAVs back to their base.
   * Steps 2-6 are executed as specified.

2. In step 1, whilst a UAV is returning to base, the mission-commander assigns it a new task.
   * 2.1 The END_MISSION command is cancelled for this UAV.
   * 2.2 The UAV commences its new mission.
   
3. In step 2, multiple UAVs have been assigned the same home coordinates.
   * 3.1 For any group of UAVs with home coordinates that violate minimum_separation_distance, the system removes the home coordinates for all except one of them.
   * 3.2 All UAVs without assigned home coordinates are assigned new in-air temporary coordinates
   * 3.3 UAVs with in-air home coordinates follow steps 3-5 until the in-air coordinates are reached and then hover in place
   * 3.4 The RPIC manually controls the landing of any UAV with in-air home coordinates.
