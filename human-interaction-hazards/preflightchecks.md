# Hazard Tree: Preflight Checks

**Description** 

Many accidents are caused by problems in preflight checks. For example, (1) turning off the GPS Fix arming check whilst running indoor maintenance tests, and forgetting to reset the check, or (2) setting the RTL altitude above the legal limit. Many prearming checks could be automated through the software, while others require consistent preflight checks, and could be supported by checklists and best practices.

[![](figures/preflightchecks.png)](#)


*Quick Links:* [PX1](#PX1) &nbsp;&nbsp; [PX2](#PX2) &nbsp;&nbsp; [PX3](#PX3) &nbsp;&nbsp; [PX4](#PX4) &nbsp;&nbsp; [PX5](#PX5) &nbsp;&nbsp; [PX6](#PX6) &nbsp;&nbsp; [PX7](#PX7)  &nbsp;&nbsp; [PX8](#PX8) &nbsp;&nbsp; [PX9](#PX9) &nbsp;&nbsp; [PX10](#PX10) &nbsp;&nbsp; [PX11](#PX11) &nbsp;&nbsp; [PX12](#PX12) &nbsp;&nbsp;   [(All Hazards)](../README.md)<br>

<sub>![](icons/h-icon.PNG)</sub> = Human Initiated Error, <sub>![](icons/s-icon.PNG)</sub> = Loss of Situational awareness, <sub>![](icons/e-icon.PNG)</sub> = Lack of Empowerment to Intervene

## <sub>![](icons/h-icon.PNG)</sub>  <a name="PX1"/> PX1: Operator places UAVs too close to each other prior to launch 
When a system involves multiple coordinated UAVs then it is important to maintain minimum separation distance. This includes the launch phase of the mission.
| <img width=120/>| Context | Solution |
|:--|:--|:--|
|PX1-S1|Multi-UAVs|RPIC receives proper training to conduct mandatory preflight checks |
|PX1-S2|Multi-UAVs|The system checks the coordinates of all UAVs on the ground and raises an alert if any of them are located less than minimum separation distance. |
|PX1-S3|Multi-UAVs|Where the system is not capable of managing collision avoidance during launch (e.g., through choreographed takeoff), then the operator should reposition the UAVs and/or carefully manage the launch and subsequent RTL. 
|PX1-S4|Multi-UAVs|If multiple UAVs are in RTL mode at the same time (even if in-air collisions are managed) then the system will check for minimum separation distance between their home coordinates and recommend remediations (e.g., staggering their return, modifying home coordinates)

## <sub>![](icons/h-icon.PNG)</sub> <a name="PX2"/> PX2: Operator places UAVs in location with insufficient clearance prior to launch 
|  <img width=120/> | Context | Solution |
|:--|:--|:--|
|PX2-1|prelaunch|Operator is trained to check for obstruction|

## <sub>![](icons/s-icon.PNG)</sub> <a name="PX3"/> PX3: The operator does not realize that a camera failure has occurred (e.g., due to servicing multiple UAVs for which only a subset of camera feeds are visible) 
|  <img width=120/> | Context | Solution |
|:--|:--|:--|
|PX4-1|Camera onboard|The operator should be able to view the camera feed from all UAVs with cameras onboard prior to launch.|
|PX4-2|Camera onboard|The system should perform a diagnostic test to make sure that the camera cap has been removed prior to launch (e.g., using onboard vision to detect cap errors).|

## <sub>![](icons/s-icon.PNG)</sub> <a name="PX4"/>  PX4: The system does not provide appropriate information regarding the geofence, so the operator is unable to determine whether it has been set correctly or not 
|  <img width=120/> | Context | Solution |
|:--|:--|:--|
|PX5-1||If the operator chooses to fly without a geofence in place, they must log their decision and rationale for foregoing the geofence.
|PX5-2||When requested, the system shall visually display a UAV's geofence on the map.
|PX5-3|Multi-UAVs|Where multiple UAVs are present, when requested by the user, the system shall visually display the outer boundary of the union of all UAVs' geofences. This increases awareness of the entire region in which UAVs are expected to fly.
|PX5-4||When requested, the system shall display all geofence-related failsafe configurations and highlight exception cases (e.g., a UAV with unexpected configurations)

## PX5: User is unaware that the system is not configured correctly <sub>![](icons/s-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX6-1||An alert shall be raised if a UAV is missing a geofence with legal altitude limits, an area greater than __minimum_area__ and less than __maximum_area__, and whose boundaries are outside the current position of the UAV|
|PX6-2|Multi-UAVs|When requested, the system shall display all geofence-related failsafe configurations and highlight exception cases (e.g., a UAV with unexpected configurations)

## PX6: User is unaware that failsafe and other flight actions are configured incorrectly (e.g., RTL actions) <sub>![](icons/s-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX7-1|preflight|The system shall store default failsafe configurations for *all* and *individual* UAVs. An alert shall be displayed if any UAV is configured differently from their default values. (Note: failsafe configurations can be set using multiple 3rd party packages, and should be checked prior to flight).

## PX7: User is unaware that critical arming  checks are disabled e.g., satellite connections, accelerometer health)] <sub>![](icons/s-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX8-1|preflight|The system shall store a list of default arming checks to be applied to all UAVs by type (e.g., PX4, Ardupilot). An alert shall be displayed if any UAV's internal configuration differs from the expected arming checks.  (Note: The list of arming checks, and their internal configurations can be set using multiple 3rd party packages, and should be automatically checked prior to flight by the system).

## PX8: User has configured autopilot in an unsafe way (e.g., setting minimum number of satelite fixes required to 1, or setting the RTL altitude illegally high or dangerously low) <sub>![](icons/h-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX9-1|preflight|The system shall store a list of default global configurations to be applied to all UAVs by type (e.g., PX4, Ardupilot). An alert shall be displayed if any UAV's internal configuration differs from its expected global configurations. (Note: The list of arming checks, and their internal configurations can be set using multiple 3rd party packages, and should be automatically checked prior to flight by the system).

## PX9: Operator attaches overly heavy or insecured payload to UAV <sub>![](icons/h-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX9-1|payload|When payload is attached the RPIC must inspect the UAV and its payload to ensure that it is valid and within acceptable payload limits as specified by the manufacturer|
|PX9-2|payload|Onboard analytics will monitor the UAV for behavior suggesting payload shifts or that the UAV is struggling to carry the payload|

## PX10: Operator fails to perform flight-readiness check and/or fix problems (e.g., dangling cables, low battery) <sub>![](icons/h-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX11-1|prelaunch|The system shall provide a check-list of preflight checks and the RPIC shall confirm the list for each UAV and for the mission as a whole|
|PX11-2|multi-UAV|When multiple UAVs are involved in the mission, the RPIC in charge of the flights shall verbally ascertain that all supporting RPICs and/or visual observers understand and acknowledge their roles in the mission.

## PX11: It is difficult for the user to check and configure multiple UAVs simultaneously. <sub>![](icons/e-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX12-1|Multi-UAVs|All preflight checks and warnings must support a multiple-UAV environment without the need for the RPIC to configure each UAV separately (unless desired)|

## PX12: The user sets switches on hand-held controller incorrectly (e.g., throttle, RTL, LAND) and as a result the UAV responds to this predefined setting immediately during a human takeover event <sub>![](icons/h-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|PX13-1|Multi-UAVs, handheld controllers as backup|Preflight checklist must include checking the positions of all switches on the handheld device.|

