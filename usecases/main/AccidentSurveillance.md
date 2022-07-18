## Use Case: Provide surveillance and information about a traffic accident

**ID**

UC3

**Description**

One or more UAVs are dispatched to a traffic accident scene in order to provide information to the emergency responders.

**Primary Actor**

* UAV&#39;s

* Drone Commander

**Supporting Actors**

* Firefighters

* Police

* Medical crews

**Stakeholders and Interests**

Having specific information about a car accident (how many cars are involved, what is the exact location, traffic jams, people injured, etc) can help emergency responders having the proper reactions.

**Pre-Conditions**

- DroneResponse system is active
- Multiple UAVs are equipped with cameras and are placed on the ground and are activated
- Approximate GPS coordinates of the accident are provided to DroneResponse

**Post Conditions**

_Success end condition:_

The accident is precisely located, the scene is described using onboard vision, and directions are generated for emergency responders

_Failure end condition:_

An accident is not found even though it has occurred

The accident site is not streamed to operators

**Trigger**

A 911 call operator receives a call reporting an accident

## **Main Success Scenario**

1. An accident report is received.
2. The route is planned and [flight authorization](../supporting/FlightAuthorization.md) is obtained.
3. The DroneResponse commander issues a command to start the mission.
5. The UAV(s) perform a [synchronized takeoff](../supporting/SynchronizedTakeoff.md).
6. The UAVs [lease airspace](../supporting/LeaseAirspace.md) and fly to the location of the accident.
7. The UAVs reach the target area and performs [image capture and analysis](../supporting/ImageCaptureAndAnalysis.md) to pinpoint the accident site and stream video.
8. A human operator inspects the video and confirms that the accident site has been correctly identified. 
9. The precise GPS coordinate of the accident and the surroundings of the road are sent to the emergency responders.
10. DroneResponse generates a route to the correct location, ensuring arrival on the correct side of the highway.
11. The UAVs continue [onboard vision and detection](../supporting/OnboardVisionAndDetection.md) to infer details of the scene  ( i.e., number of cars, presence of fire, victims on the ground, toxic material leakage).
12. Specific information gathered by UAV's is processed and classified into specific emergency categories and sent to related emergency services. (Traffic information sent to the police, accident structure information sent to the fire fighters, human related information sent to medical staff).
13. Emergency responders arrive on the scene.
14. The Drone Commander [ends the mission](../supporting/EndMission.md)

## Exceptions

1. All [general exceptions](../../README.md#GeneralExceptions) apply.

2. In step 7, after scanning the vicinity of the reported accident three times, the UAVs are unable to locate the accident.
   * 2.1 An alert is raised that the accident can't be located
   * 2.2 DroneResponse displays images from the camera of each drone
   * 2.3 The operator checks the images
      * 2.3.1 If the operator identifies the accident they mark it manually on the map and the UAVs stream video for the marked region.  The use case continues with step 9.
      * 2.3.2 If the operator cannot identify the accident, then the use case continues with step 14. 

3. In step 8, the UAV detects a possible accident site at a confidence level below `victim\_detected` threshold but above the lowest ignore level.
   * 3.1 The UAV logs the alert including saved imagery
   * 3.2 DroneResponse saves the GPS coordinates of the sighting
   * 3.3 The UAV continues to scan the location of the accident. 

## Resources Used

1. [https://www.researchgate.net/publication/313693086\_Using\_drones\_for\_automatic\_monitoring\_of\_vehicular\_accident](https://www.researchgate.net/publication/313693086_Using_drones_for_automatic_monitoring_of_vehicular_accident)

2. [https://www.ncbi.nlm.nih.gov/pubmed/32183069](https://www.ncbi.nlm.nih.gov/pubmed/32183069)

<br><br>
[Return to use case list](../../README.md) 
