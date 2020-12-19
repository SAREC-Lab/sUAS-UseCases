## Exception Case: Loss of Signal

**ID**
EC1

**Description**

Without an onboard pilot, there is a significant reliance on the command and control link, and a greater emphasis on the loss of functionality associated with lost of signal.
This exception case occurs when such a loss of signal occurs.  Most UAVs have some degree of onboard autonomy - varying between the ability to continue flight to the currently assigned
waypoint, execute failsafe mechanisms, and/or complete an entire mission autonomously.

**Assumptions**

UAVs are operating in the USA with two available radio frequencies. 2.4Ghz is used for communication over the hand-held GCS (i.e., for manual control), while the 
900Mhz frequency is used for computer-managed communication from DroneResponse to the UAV.  Actual frequencies differ in different countries and so we refer to these
as [MANUAL_FREQUENCY] and [MISSION_FREQUENCY].

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
- A [failsafe] action has been established prior to flight to automatically activate RTL (Return to Launch) at a predefined altitude when loss-of-signal occurs.

**Post Conditions**

Success end condition

Either:
- Signal is re-established and the flight continues
- The UAV is landed safely and quickly despite loss of link
- The UAV completes its mission as planned despite loss of signal (Note: This is currently not authorized by FAA)

Failure end condition:

- The UAV is lost and/or crashes.

**Trigger**

The UAV is in flight and loss-of-signal occurs for greater than [loss_of_signal_threshold_seconds].

## Main Scenario

Steps 1 and 2 occur simultaneously

1. The UAV detects and responds to loss-of-signal
   * 1.1 The UAV detects that it has lost communication with the ground control station.
   * 1.2 The failsafe mechanism is activated and the RTL autonomously returns home at its uniquely assigned RTL altitude.

2. DroneResponse responds to the loss-of-signal
   * 2.1 The runtime monitoring system detects a loss of signal event for a UAV
   * 2.2 The runtime monitoring system raises an alert
   * 2.3 The alert is displayed in the UI in order to notify the RPIC of the loss-of-signal event
   
3. The RPIC maintains visual line of sight with the UAV and observes that it has transitioned to RTL state.
4. If necessary, the UAV suspends the remainder of the mission or manually moves other UAVs out of the way of the returning UAV.

## Exceptions

1. All ubiquitous exceptions are handled.

2. In step 1, no failsafe mechanism has been established onboard the UAV.
   * 1.1 If the UAV flies outside of an established Geofence then the Geofence_failsafe is activated.

3. In step 2, multiple UAVs experience simultaneous loss of signal and their RTLs are simultaneously activated. Each UAV has a unique RTL altitude. <br> One of the following sub-cases occurs:
   * 3.1 Each UAV has a unique altitude assigned and returns home safely (luckily) avoiding collision with other UAVs upon ascending and descending. (Note: Currently all UAV failsafes operate on a single UAV and are optimized for that UAV without considering multi-UAV collisions).
   * 3.2 Each UAV has not been assigned a unique altitude, thereby increasing the risk of collisions during simultaneous RTL events.
   
4. In step 1.2, signal is restablished during RTL. 
   * 4.1 ATC runs a diagnostic of each UAVs flight path and attempts to [Reserve Airspace](ReservedAirspace.md) for the entire RTL flight. 
   * 4.2 When airspace cannot be reserved for the entire route the UAV [Reserves Airspace](ReservedAirspace.md) for as much of the route as available. The UAVs mode is reset to FLYING.
   * 4.3 When the UAV reaches its intermediate waypoint, it attempts to [Reserve Airspace](ReservedAirspace.md) for the remainder of the flight.
   * 4.4 Steps 4.2 and 4.3 are repeated until the UAV receives clearance to return home.


   
