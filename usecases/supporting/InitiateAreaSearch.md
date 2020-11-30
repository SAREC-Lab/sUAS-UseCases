(Needs fixing)

## Use Case: Initiate Area Search

**ID** : SPLC-1001

**Description**

Define search area and allocate routes to UAV(s)

**Invoked by**
[IceRescue](../main/IceRescue.md), [RiverRescue](../main/RiverRescue.md)

**Primary Actor**

Drone Commander

**Supporting Actors**

Semi-autonomous UAV

**Stakeholders and Interests**

**Pre-Conditions**

- UAVs active and registered with Dronology
- DroneResponse is active

**Post Conditions**

Success end condition

Search routes planned and allocated to UAVs for an efficient search.

Failure end condition:
 Ineffective search routes provide low coverage or inefficient search

**Trigger**

An emergency responder chooses to define a search

## Main Success Scenario

1. Mission commander marks the search area on the map.
2. The system checks the validity of the search area and retrieves current NOTAMs.
3. Mission commander selects one, several, or all available UAVs to participate in the search.
4. DroneResponse generates an efficient search plan for the selected UAVs to cover the marked area.
5. Dronology assigns search routes to each selected UAV.

## Exceptions

1. In step 2, the search area includes no-fly zones.

   * 1.1 The system adds no-fly areas to the marked search area.

2. In step 3, insufficient UAVs are available with correct equipment for the search.

   * 2.1 The mission commander requests additional UAVS and/or additional equipment be added to the drone fleet.

   * 2.2 The Drone technician adds requested drones and/or equipment if available.
