**DroneResponse Use Cases**

**Use Case:** Image Capture and Analysis

**Description**

UAV collects imagery using an onboard camera and analyzes that imagery in real-time to identify specific objects and raise detection events.

**Primary Actor**

Semi-Autonomous UAV

**Supporting Actors**

Mission Commander
Onboard vision model

**Stakeholders and Interests**

**Pre-Conditions**
- UAV is in the air 
- UAV has a functioning RGB or thermal camera
- UAV has a trained vision model onboard that is capable of detecting objects of interest
- Videostream server is active and UAV is registered with the videostream server

**Post Conditions**

Success end condition

- UAV detects and annotates objects of interest within the region of interest at high degrees of accuracy [metric needed]
- Annotated video is streamed to the videostream server

Failure end condition:
- Target objects within the UAVs field of view are not detected 

**Trigger**

The UAV receives a command to collect and analyze imagery

## Main Success Scenario

1. If the camera is not activated, the UAV activates it.
2. The UAV streams imagery to its onboard companion computer.
3. Onboard compute processes streamed imagery and annotates objects of interest to depict their bounding boxes and confidence scores.
4. When an object is detected with confidence greater than the current [VisionDetection_Threshold] value, an event is raised and forwarded to the DroneResponse Event Manager.
5. All collected image streams (with and without annotations) are transmitted to the videostream server.
6. Steps 2-5 are continually repeated until the UAV is commanded to stop collecting imagery.

## Exceptions

1. All [general exceptions](../../README.md#GeneralExceptions) apply.
