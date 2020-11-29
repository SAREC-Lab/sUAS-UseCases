##Use Case: Activate and Arm

**Description**

The UAV is prepped for flight, activated by turning 'safety' off, and finally armed.

**Invoked by**
[IceRescue](../main/IceRescue.md), [RiverRescue](../main/RiverRescue.md), [AccidentSurveillance](../main/AccidentSurveillance.md), [AirSampling](../main/AirSampling.md), [WaterSampling](../main/WaterSampling.md), [DefibrillatorDelivery](../main/DefibrillatorDelivery.md), [StructuralFire](../main/StructuralFire.md)

**Primary Actor**

RPIC

**Supporting Actors**

Technicians

**Stakeholders and Interests**

General public

**Pre-Conditions**

- UAV has been prepped for flight with batteries, propellers etc and is airworthy
- UAV has been placed at its launching location

**Post Conditions**

Success end condition

- The UAV passes arming checks and is armed for flight

Failure end condition:
- The UAV takes off without adequate arming checks
- The UAV fails to arm

**Trigger**

An arming command is issued

## Main Success Scenario

1. Steps go here.
2. More steps here. (coming soon)

## Specific Exceptions


## General Exceptions



