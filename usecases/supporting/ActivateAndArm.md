## Use Case: Activate and Arm

**ID**

SC1

**Description**

The UAV is prepped for flight, activated by turning 'safety' off, and finally armed.

**Invoked by**


| [River and Ice Rescue](../main/RiverRescue.md) | [Item Delivery](../main/ItemDelivery.md)| [AccidentSurveillance](../main/AccidentSurveillance.md) | [StructuralFire](../main/StructuralFire.md) | [EnvironmentalSampling](../main/EnvironmentalSampling.md) |
| :------: | :--------: | :--------: | :------: |:------: |
| x | x | x | x | x|

**Primary Actor**

- RPIC

**Supporting Actors**

-  Technicians

**Stakeholders and Interests**

-  General public

**Pre-Conditions**

- UAV has been prepped for flight with batteries, propellers, etc. and is airworthy
- UAV has been placed at its launching location

**Post Conditions**

_Success end condition:_

The UAV passes arming checks and is armed for flight

_Failure end condition:_ 

The UAV takes off without adequate arming checks

The UAV fails to arm

**Trigger**

An arming command is issued

## Main Success Scenario

1. The RPIC deactivates the UAV's safety switch.
2. DroneResponse issues an arming command.
3. The UAV executes all prearming tests.
4. The UAV passes prearming tests.
5. The UAV arms.
6. The UAV's status is set to MISSION mode (PX4=MISSION, Ardupilot=GUIDED/STABILIZED)
7. The UAV's automated pilot notifies DroneResponse that the UAV is armed for flight.

## Exceptions

1. All [general exceptions](../../README.md#GeneralExceptions) apply, except for those with [in_air] preconditions.

2. In step 1, the RPIC fails to deactivate the safety switch
   * 2.1 In step 2, the UAV issues a warning sound and raises an error when the arming command is attempted.
   * 2.2 The use case continues from Step 1.
   
3. In step 4, the UAV fails to pass its prearming tests
   * 3.1 The system reports specific reasons for prearming failure.
   * 3.2 The RPIC reactivates the UAV's safety switch.
   * 3.3 A technician attempts to fix the root cause of the prearming failure (e.g., recalibrating the UAV)
      * 3.3.1 If the technician fixes the problem, the use case restarts from Step 1.
      * 3.3.2 If the technician fails to fix the problem, the UAV is removed from service.

<br><br>
[Return to use case list](../../README.md) 
