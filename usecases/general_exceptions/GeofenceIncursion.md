## Exception Case: Geofence incursion

**ID**

EC2

**Description**

A Geofence establishes a virtual boundary around a geographical location. Most sUAS provide 
support for establishing a geofence based on GPS coordinates and maximum altitude.  Geofences can
be established over rectangular, circular, or polygonic regions of a map.  If a UAV breaches its geofence
then a failsafe mechanism will activate causing the UAV to RTL or LAND in place. In many cases, the
UAV supports a measured response with at least two trigger points associated with [Approaching_Geofence] and
[Geofence_Breach].


**Assumptions**

The UAV supports geofencing and software is available for configuring the geofence.

**Primary Actor**

- RPIC
- Unmanned Aerial Vehicle

**Supporting Actors**

- Air Traffic Control

**Stakeholders and Interests**

- RPIC
- General public

**Pre-Conditions**

- A [failsafe] action has been established prior to flight to automatically activate RTL 
(Return to Launch) or [land in place] if the UAV breaches the geofence.
- The UAV was launched from within the geofence
- The Geofence has been established correctly around the intended flight path of the UAV.

**Post Conditions**

Success end condition

Either:
- The UAV does not fly outside of the geofence during its mission

Failure end condition:

- The UAV flies outside the geofence.

**Trigger**

The UAV is armed and a Geofence alert (i.e., either [Approaching_Geofence] or [Geofence_breach] occur.

## Main Scenario

1. DroneResponse responds to the `[APPROACHING_GEOFENCE]` battery alarm
   * 1.1 The runtime monitoring system detects that the UAV is approaching the geofence
   * 1.2 The runtime monitoring system raises an alert
   * 1.3 The current flight route is cancelled
   * 1.4 The alert is displayed in the UI in order to notify the RPIC of the low battery warning for the UAV
   * 1.5 The system either:
      * 1.5.1 Reroutes the UAV so that it avoids flying close to the geofence
	  * 1.5.2 The operator intervenes and issues a new flight command to the UAV
   
2. The UAV detects a `[GEOFENCE_BREACH]`
    * 2.1 The The failsafe mechanism is activated according to the UAVs preconfiguration (e.g. RTL or land in place)
   
3. The RPIC maintains visual line of sight with the UAV until it RTLs or LANDs.

4. If necessary, the UAV suspends the remainder of the mission or manually moves other UAVs out of the way of the returning UAV.

## Exceptions

1. All ubiquitous exceptions are handled.

2. In step 1.3, the RPIC decides that the current task can not be continued by the UAV.
   * 2.1 The RPIC decides that the UAV can not complete its designated task during the mission and is relived from its task.
   * 2.2 The RPIC manually activates RTL for the UAV.
   * 2.3 DroneResponse provdes an option to assign another UAV with the task.
   * 2.4 The RPIC assigns a new UAV with the task and the mission continues.


3. In step 2, no failsafe mechanism has been established onboard the UAV.
   * 3.1 The runtime monitoring system raises a geofence_breach alert.
   * 3.2 The RPIC immediately lands the UAV in place or manually activates RTL for the UAV.

   


   
