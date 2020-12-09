## Hazard Tree: Preflight Checks

Intro goes here.

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
|UX1-|Context here|Requirement here|

## PX3: The operator is unable to rectify the camera failure during flight. <sub>![](icons/e-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|UX1-|Context here|Requirement here|

## PX4: The operator does not realize that a camera failure has occurred (e.g., due to servicing multiple UAVs for which only a subset of camera feeds are visible) <sub>![](icons/s-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|UX1-|Context here|Requirement here|

## PX5: The system does not provide appropriate information regarding the geofence, so the operator is unable to determine whether it has been set correctly or not <sub>![](icons/s-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|UX1-|Context here|Requirement here|

## PX6: User is unaware that the system is not configured correctly <sub>![](icons/s-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|UX1-|Context here|Requirement here|

## PX7: User is unaware that failsafe and other flight actions are configured incorrectly (e.g., RTL actions) <sub>![](icons/s-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|UX1-|Context here|Requirement here|

## PX8: User is unaware that critical arming  checks are disabled e.g., satellite connections, accelerometer health)] <sub>![](icons/s-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|UX1-|Context here|Requirement here|

## PX9: User has configured autopilot in an unsafe way (e.g., setting minimum number of satelite fixes required to 1, or setting the RTL altitude illegally high or dangerously low) <sub>![](icons/h-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|UX1-|Context here|Requirement here|

## PX10: User has disabled critical arming checks prior to launch (e.g., deactivating the GPS fix during indoor maintenance) <sub>![](icons/h-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|UX1-|Context here|Requirement here|

## PX11: Operator attaches overly heavy or insecured payload to UAV <sub>![](icons/h-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|UX1-|Context here|Requirement here|

## PX12: Operator fails to perform flight-readiness check and/or fix problems (e.g., dangling cables, low battery) <sub>![](icons/h-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|UX1-|Context here|Requirement here|

## PX13: It is difficult for the user to check and configure multiple UAVs simultaneously. <sub>![](icons/e-icon.PNG)</sub>
| Hazard addressed | Context | Solution |
|:--|:--|:--|
|UX1-|Context here|Requirement here|
