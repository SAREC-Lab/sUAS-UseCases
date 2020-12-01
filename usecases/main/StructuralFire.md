## Use Case: Structural fire fighting

**Description**

Multiple UAVs dispatched to analyze the structure for fire fighting

**Primary Actor**

Drone Commander

**Supporting Actors**

Semi-autonomous UAV

**Stakeholders and Interests**

Fire department engaged in fire fighting
FAA concerned with flight regulations
General public

**Pre-Conditions**

- DroneResponse is running
- Multiple UAVs are equipped with cameras
- A victim is in the river

**Post Conditions**

Success end condition

The UAV creates and maintains a heatmap of the entire building
All UAVs return to launch without damage at the end of the incident

Failure end condition:

A UAV collides with the building or ground
The UAVs fail to provide an accurate heatmap of the building 


**Trigger**

The Drone Commander activates the fire support mission.

## Main Success Scenario

1. Firefighters request [flight authorization](../supporting/FlightAuthorization.md)
2. UAVs are [activated and armed](../supporting/ActivateAndArm.md)
3. The UAVs [perform synchronized takeoff](../supporting/SynchronizedTakeoff.md)
4. The UAVs use their onboard vision to create an initial mapping of the building.
5. The UAVs plan optimized and coordinated surveillance flights around the building.
6. Each UAV performs [image capture and analysis](../supporting/ImageCaptureAndAnalysis.md) using thermal imagery.
7. Imagery from each UAV is continuously streamed and aggregated to create a current heatmap of the building.
8. Steps 4-7 are repeated throughout the fire event
9. The Incident Commander [ends mission](supporting/EndMission.md) once the fire has been controlled.

## Exceptions

1. All [general exceptions](../../README.md#GeneralExceptions) apply.

2. In step 6, the UAV detects a possible victim at a confidence level below [victim_detected] threshold but above the lowest [ignore_level]
   * 2.1 The UAV raises an alert and requests [victim_confirmation](../supporting/VictimConfirmation.md) from the human operator.
   * 2.2 The UAV continues to stream imagery
   * 2.2 The human operator inspects the video stream
      * 2.2.1 If the human operator believes that a victim may have been found, firefighters plan and execute a rescue mission.
      * 2.2.2 If the human operator rejects the candidate sighting, the UAV continues its currently assigned route.

## Resources Used

1. [https://www.semanticscholar.org/paper/Unmanned-Aerial-Systems-in-the-Fire-Service%3A-and-Griffith-Wakeham/a34e38307a88fda699da7d1aa6d64231ff717d55](https://www.semanticscholar.org/paper/Unmanned-Aerial-Systems-in-the-Fire-Service%3A-and-Griffith-Wakeham/a34e38307a88fda699da7d1aa6d64231ff717d55)

