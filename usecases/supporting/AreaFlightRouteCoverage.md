## Use Case: Generate Flight Routes for Area Coverage

**ID**

SC3


**Description**

Define a coverage area and allocate routes to UAV(s)

**Invoked by**

| [River and Ice Rescue](../main/RiverRescue.md) | [Item Delivery](../main/ItemDelivery.md)| [AccidentSurveillance](../main/AccidentSurveillance.md) | [StructuralFire](../main/StructuralFire.md) | [EnvironmentalSampling](../main/EnvironmentalSampling.md) |
| :------: | :--------: | :--------: | :------: |:------: |
| x |   |   |   | x|

**Primary Actor**

- Drone Commander

**Supporting Actors**

- Semi-autonomous UAV

**Stakeholders and Interests**

**Pre-Conditions**

- UAVs are active and armed
- DroneResponse is active

**Post Conditions**

_Success end condition:_

Search routes planned and allocated to UAVs for an efficient search.

_Failure end condition:_

 Ineffective search routes provide low coverage or inefficient search

**Trigger**

User selects the option to mark a region and generate routes dynamically

## Main Success Scenario

1. A user selects the feature to mark a region on the currently displayed map.
2. The user marks a polygon shape on the map.
3. DroneResponse analyzes the shape and size of the drawn polygon for feasibility of generating routes and the polygon is accepted as viable for route generation.
4. The user specifies the number of UAVs `N` that will participate in the mission.
5. DroneResponse dynamically generates an efficent set of `N` flight routes that optimize coverage of the marked area whilst minimizing flight times.
6. DroneResponse assigns the flight routes to  `N` available UAVs.
7. The use case ends once flight routes have been generated and assigned.

## Alternative Steps

1. In step 5, instead of optimizing for area coverage, the algorithm optimizes the routes for a sampling mission
   * 1.1 The user specifies the number of samples `S` to be collected by each UAV
   * 1.2 The algorithm optimizes the flight paths such that `S` sampling locations are distributed as evenly as possible over the marked area, locations are clustered into `N` flight paths, and each UAV's flight path is optimized to reduce power consumption.

## Exceptions

1. All [general exceptions](../../README.md#GeneralExceptions) apply.

2. In step 1, the user wishes to mark a search area that is not entirely covered by the currently displayed map view.
   * 2.1 If the search area is in the vicinity of the currently displayed map view, the user pans and rescales the map until the planned search area is encompassed by the view.
   * 2.2 If the search area is not in the vicinity of the currently displayed map view, the user recenters the map by entering GPS coordinates.

3. In step 3, the polygon is deemed infeasible for route generation.
   * 3.1 If the polygon has insufficient width or height it is rejected.
   * 3.2 If the polygon includes unsupportable indentations or appendages these will be ignored during the flight route generation and an alert will be raised.

4. In step 4, there are less than `N` UAVs available for assignment to the designated flight plans. Either
   * 4.1 The user reduces the number of designated UAVs to a number for which viable UAVs are available
   * 4.2 or a technician activates and arms additional UAVs for inclusion in the mission.
   

   
[Return to use case list](../../README.md)
