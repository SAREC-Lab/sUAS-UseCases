## Use Case: Collect environmental sample

**ID**

SC4


**Description**

UAV collects an environmental sample (e.g., air or water) and optionally performs a dynamic analysis. A targeted collection point can be either on the 
surface (e.g., water collection) or at a designated altitude (e.g., air sampling).


**Invoked by**


| [River and Ice Rescue](../main/RiverRescue.md) | [Item Delivery](../main/ItemDelivery.md)| [AccidentSurveillance](../main/AccidentSurveillance.md) | [StructuralFire](../main/StructuralFire.md) | [EnvironmentalSampling](../main/EnvironmentalSampling.md) |
| :------: | :--------: | :--------: | :------: |:------: |
|  |  |   |  | x |

**Primary Actor**

- Semi-Autonomous UAV

**Supporting Actors**

- Mission Operator

**Pre-Conditions**

- The UAV has arrived at a predefined sampling location

**Post Conditions**

_Success end condition:_

Samples are collected and analyzed from all targeted coordinates

_Failure end condition:_

UAV fails to collect samples

**Trigger**

The UAV reaches the GPS coordinates of the first sample collection waypoint

## Main Success Scenario

1. The UAV arrives at its designated collection coordinates.

2. The UAV positions itself to collect a water sample.
   * 2.1 The UAV uses its onboard vision capabilities to find an unobstructed route (e.g., free of tree branches) to the water.
   * 2.2 The UAV begins its descent whilst using [image capture and analysis](ImageCaptureAndAnalysis.md) and altitude sensors to position itself correctly above the water.
   
3. The UAV activates its onboard collection device and collects a water sample.
   * 3.1 The UAV lowers its collection apparatus (typically a rubber hose, powered by a pump).
   * 3.2 The UAV collects the water sample.
   * 3.3 The UAV stores the water sample for carrying home.

3. Steps 1-3 are repeated until all planned collection points have been visited or the UAV has used all of its collection resources.

4. The use case finishes when the UAV commences its flight home.

## Alternative Steps

1. In step 2, the UAV is tasked with collecting an air sample instead of a water sample. Step 2 is skipped and the use case continues with step 3.

2. In step 3, the UAV not only collects a sample (air or water), but performs onboard analysis.
   * 2.1 The UAV performs onboard analysis of the sample.
   * 2.2 Targeted pollutants are identified in the sample.
      * 2.2.1 The UAV dynamically plans a new collection route (e.g., to collect additional samples from the local area).
	  * 2.2.2 The use case resumes at Step 1 using the dynamically planned collection points instead of preplanned ones.
   * 2.3 If no pollutants are identified in the sample, then the use case continues with Step 1 using the preplanned collection points.

## Exceptions

1. All [general exceptions](../../README.md#GeneralExceptions) apply.

2. In step 2 the UAV is unable to find an unobstructed route to the water in the vicinity of the target waypoints and requests advice from the user. Either:
   * 2.1 The user directs the UAV to skip the current waypoint.
   * 2.2 The user leverages the UAVs' onboard camera controls to manually identify an unobstructed route to the water. The User either manually flies the UAV through the new route or marks the route for the UAV to perform automatically. 



[Return to use case list](../../README.md)
