## Exception Case: Low Battery

**ID**

EC3

**Description**

Most UAVs are equiped with Lithium polymer batteries (LiPo) - varying in terms of number of cells, voltage and capacity. 
Depending on the size, weight, and the payload a UAV is carrying, typical flying areas range from 15-40 minutes. 


**Assumptions**

UAVs are battery powered with a `[BATTERY_CAPACITY]` and `[MAX_BATTERY_VOLTAGE]`.

**Primary Actor**

- Ground Control System
- RPIC
- Unmanned Aerial Vehicle

**Supporting Actors**

- Air Traffic Control

**Stakeholders and Interests**

- RPIC
- General public

**Pre-Conditions**

- The UAV is in the air and has a command and control link to one or more ground control stations
- A [failsafe] action has been established prior to flight to automatically activate RTL (Return to Launch) if the battery level falls below a certain `[CRITICAL_BATTERY_THRESHOLD]`

**Post Conditions**

Success end condition

Either:
- The UAV is landed safely when a low battery warning occurs
- The UAV completes its mission as planned despite low battery warning

Failure end condition:

- The UAV crashes or lands in an unsafe area.

**Trigger**

The UAV is in flight and a low battery alarm, with the bettery level smaller than `[LOW_BATTERY_THRESHOLD]` is raised.

## Main Scenario

1. DroneResponse responds to the battery alarm
   * 1.1 The runtime monitoring system detects a low bettery event for a UAV
   * 1.2 The runtime monitoring system raises an alert
   * 1.3 The alert is displayed in the UI in order to notify the RPIC of the low battery warning for the UAV
   
   
2. The UAV detects a battery level below `[CRITICAL_BATTERY_THRESHOLD]`
    * 2.1 The The failsafe mechanism is activated and the RTL autonomously returns home at its uniquely assigned RTL altitude.
   
3. The RPIC maintains visual line of sight with the UAV and observes that it has transitioned to RTL state.

4. If necessary, the UAV suspends the remainder of the mission or manually moves other UAVs out of the way of the returning UAV.

## Exceptions

1. All ubiquitous exceptions are handled.

2. In step 1.3, the RPIC decides that the current task can not be continued by the UAV.
   * 2.1 The RPIC decides that the UAV can not complete its designated task during the mission and is relived from its task.
   * 2.2 The RPIC manually activates RTL for the UAV.
   * 2.3 DroneResponse provdes an option to assign another UAV with the task.
   * 2.4 The RPIC assigns a new UAV with the task and the mission continues.


3. In step 2, no failsafe mechanism has been established onboard the UAV.
   * 3.1 The runtime monitoring system raises a critical battery alarm.
   * 3.2 The RPIC immediately lands the UAV in place or manually actiavtes RTL for the UAV.

   


   
