**DroneResponse Use Cases**

**Use Case:** Perform Search

**ID** : SPLC-1002

**Description**

UAV performs its predefined search

**Primary Actor**

Semi-Autonomous UAV

**Supporting Actors**

Mission Commander

**Stakeholders and Interests**

**Pre-Conditions**

- Each UAV has been assigned a search mission defined by as series of waypoints
- Each UAV is at its own starting waypoint of the designated search.

**Post Conditions**

Success end condition

UAVs search the designated area and if a target is along the route, the target is found.

Failure end condition:
 UAV fails to execute the designated search.

**Trigger**

The UAV reaches the GPS coordinates of its first waypoint.

## Main Success Scenario

1. The UAV activates its camera (if not already activated).
2. The UAV commences to fly its designated routes at the specified velocity.
3. The UAV streams imagery to its onboard companion computer and to DroneResponse.
4. Each UAV&#39;s onboard compute processes imagery from its camera using a trained vision model [$VISION\_MODEL$]
5. When a UAV flies within vision range of a victim, its onboard image recognition software detects the victim.
6. When image recognition is greater than the [$image\_recognition\_threshold$], the UAV raises a victim\_alert.

##


## Exceptions

1. **At any time** , communication is lost between the Ground Control Station and a UAV.
   * See **Lost Drone-to-GCS Communication** (SPLC-2001)

1. At any time, a malfunction error is raised by a UAV in flight.
   * See **Drone-in-flight Malfunction Alert** (SPLC-XXXX)

3. In step 6, the UAV detects a possible target at a confidence level below [$image\_recognition\_threshold$] but above the lowest `ignore&#39; level.

   * 3.1 The UAV logs the alert including saved imagery

   * 3.2 DroneResponse saves the GPS coordinates of the sighting

   * 3.3 The UAV continues its currently assigned route.

   * 3.4 The back-up operator reviews the streamed imagery

   * 3.5 The back-up operator confirms that the sighting is not a victim.