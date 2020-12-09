## Hazard Tree: Preflight Checks

[![](figures/preflightchecks.png)](#)

<sub>![](icons/h-icon.PNG)</sub> = Human initiated error, <sub>![](icons/s-icon.PNG)</sub> =Loss of Situational awareness, <sub>![](icons/e-icon.PNG)</sub> = Lack of empowerment to intervene  <br>[(Return to list of hazard trees)](../README.md)<br>

<br>:construction: Need to add mitigations.

## PX1: Operator places UAVs too close to each other prior to launch <sub>![](icons/h-icon.PNG)</sub>
When a system involves multiple coordinated UAVs then it is important to maintain minimum separation distance. This includes the launch phase of the mission.
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX1-1|Multi-UAVs|RPIC receives training |
|PX1-2|Multi-UAVs|The system checks the coordinates of all UAVs on the ground and raises an alert if any of them are located less than minimum separation distance. |
|PX1-3|Multi-UAVs|Where the system is not capable of managing collision avoidance during launch (e.g., through choreographed takeoff), then the operator should reposition the UAVs and/or carefully manage the launch and subsequent RTL. 
|PX1-4|Multi-UAVs|If multiple UAVs are in RTL mode at the same time (even if in-air collisions are managed) then the system will check for minimum separation distance between their home coordinates and recommend remediations (e.g., staggering their return, modifying home coordinates)

## PX2: Operator places UAVs in location with insufficient clearance prior to launch <sub>![](icons/h-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX2-1|prelaunch|Operator is trained to check for obstruction|

## PX3: The operator is unable to rectify the camera failure during flight. <sub>![](icons/e-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX3-1-|Camera onboard|The UI should enable the user to perform basic diagnostics and to activate (or reactivate) the camera remotely.|

## PX4: The operator does not realize that a camera failure has occurred (e.g., due to servicing multiple UAVs for which only a subset of camera feeds are visible) <sub>![](icons/s-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX4-1|Camera onboard|The operator should be able to view the camera feed from all UAVs with cameras onboard prior to launch.|
|PX4-2|Camera onboard|The system should perform a diagnostic test to make sure that the camera cap has been removed prior to launch (e.g., using onboard vision to detect cap errors).|

## PX5: The system does not provide appropriate information regarding the geofence, so the operator is unable to determine whether it has been set correctly or not <sub>![](icons/s-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX5-1||If the operator chooses to fly without a geofence in place, they must log their decision and rationale for foregoing the geofence.
|PX5-2||When requested, the system shall visually display a UAV's geofence on the map.
|PX5-3|Multi-UAVs|Where multiple UAVs are present, when requested by the user, the system shall visually display the outer boundary of the union of all UAVs' geofences. This increases awareness of the entire region in which UAVs are expected to fly.
|PX5-4||When requested, the system shall display all geofence-related failsafe configurations and highlight exception cases (e.g., a UAV with unexpected configurations)

## PX6: User is unaware that the system is not configured correctly <sub>![](icons/s-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX6-1||An alert shall be raised if a UAV is missing a geofence with legal altitude limits, an area greater than __minimum_area__ and less than __maximum_area__, and whose boundaries are outside the current position of the UAV|
|PX6-2|Multi-UAVs|When requested, the system shall display all geofence-related failsafe configurations and highlight exception cases (e.g., a UAV with unexpected configurations)

## PX7: User is unaware that failsafe and other flight actions are configured incorrectly (e.g., RTL actions) <sub>![](icons/s-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX7-1|preflight|The system shall store default failsafe configurations for *all* and *individual* UAVs. An alert shall be displayed if any UAV is configured differently from their default values. (Note: failsafe configurations can be set using multiple 3rd party packages, and should be checked prior to flight).

## PX8: User is unaware that critical arming  checks are disabled e.g., satellite connections, accelerometer health)] <sub>![](icons/s-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX8-1|preflight|The system shall store a list of default arming checks to be applied to all UAVs by type (e.g., PX4, Ardupilot). An alert shall be displayed if any UAV's internal configuration differs from the expected arming checks.  (Note: The list of arming checks, and their internal configurations can be set using multiple 3rd party packages, and should be automatically checked prior to flight by the system).

## PX9: User has configured autopilot in an unsafe way (e.g., setting minimum number of satelite fixes required to 1, or setting the RTL altitude illegally high or dangerously low) <sub>![](icons/h-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX9-1|preflight|The system shall store a list of default global configurations to be applied to all UAVs by type (e.g., PX4, Ardupilot). An alert shall be displayed if any UAV's internal configuration differs from its expected global configurations. (Note: The list of arming checks, and their internal configurations can be set using multiple 3rd party packages, and should be automatically checked prior to flight by the system).

## PX10: Operator attaches overly heavy or insecured payload to UAV <sub>![](icons/h-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX9-1|payload|When payload is attached the RPIC must inspect the UAV and its payload to ensure that it is valid and within acceptable payload limits as specified by the manufacturer|
|PX9-2|payload|Onboard analytics will monitor the UAV for behavior suggesting payload shifts or that the UAV is struggling to carry the payload|

## PX11: Operator fails to perform flight-readiness check and/or fix problems (e.g., dangling cables, low battery) <sub>![](icons/h-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX11-1|prelaunch|The system shall provide a check-list of preflight checks and the RPIC shall confirm the list for each UAV and for the mission as a whole|
|PX11-2|multi-UAV|When multiple UAVs are involved in the mission, the RPIC in charge of the flights shall verbally ascertain that all supporting RPICs and/or visual observers understand and acknowledge their roles in the mission.

## PX12: It is difficult for the user to check and configure multiple UAVs simultaneously. <sub>![](icons/e-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX12-1|Multi-UAVs|All preflight checks and warnings must support a multiple-UAV environment without the need for the RPIC to configure each UAV separately (unless desired)|

## PX13: If the operator assumes manual control during the mission and switches (e.g., throttle) are set incorrectly, the UAV could respond dramatically (e.g., plunging to the ground). <sub>![](icons/e-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX13-1|Multi-UAVs, handheld controllers as backup|Preflight checklist must include checking the positions of all switches on the handheld device.|

