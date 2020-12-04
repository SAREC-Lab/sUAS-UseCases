# Use Cases for Emergency Response Missions with Small Unmanned Aerial Systems

If you would like to use these use-cases we ask you to reference our paper: <br><br>
**Jane Cleland-Huang, Ankit Agrawal, Md Nafee Al Islam, Eric Tsai, Maxime Van Speybroeck, Michael Vierhauser:
``Requirements-Driven Configuration of Emergency Response Missions with Small Aerial Vehicles''. Software Product Line Conference (SPLC) 2020: 26:1-26:12**
([bib available here](SPLC2020.txt))

Special thanks to the South Bend Fire Fighters for all of their input.

Please note: The import and inter-linking of these uses cases is in progress.

### Main Use Cases

| Use Case      | Description                 | Contrib. Stakeholders              | Main Use Case  |
| ------------- |-------------                    | -----                              |            -----|    
| UC1           | River and Ice Search & Rescue           | South Bend Firefighters |[RiverRescue.md](usecases/main/RiverRescue.md ) 
| UC2           |Item Delivery         |    DeLive, Cardiac Science | [ItemDelivery.md](usecases/main/ItemDelivery.md)
| UC3           |Traffic Accidents                |    South Bend Firefighters | [AccidentSurveillance.md](usecases/main/AccidentSurveillance.md)
| UC4           | Structural Fires                |    South Bend Firefighters | [StructuralFire.md](usecases/main/StructuralFire.md)
| UC5           | Environmental Sampling  (air & water)               |    Environmental Scientists | [EnvironmentalSampling.md](usecases/main/EnvironmentalSampling.md)


### Supporting Use Cases

| Use Case      | Description                  | Link  |
| ------------- |-------------                    | -----     |
| SC1           | Activate and Arm | [ActivateAndArm.md](usecases/supporting/ActivateAndArm.md)|
| SC2           | Active Tracking  | [ActiveTracking.md](usecases/supporting/ActiveTracking.md)|
| SC3           | Area Flight Route Coverage | [AreaFlightRouteCoverage.md](usecases/supporting/AreaFlightRouteCoverage.md)|
| SC4           | Collect and Analyze Sample | [CollectAndAnalyseSample.md](usecases/supporting/CollectAndAnalyseSample.md)|
| SC5           | End Mission  | [EndMission.md](usecases/supporting/EndMission.md)|
| SC6           | Flight Authorization  | [FlightAuthorization.md](usecases/supporting/FlightAuthorization.md)|
| SC7           | Fly to destination |[FlyToDestination.md](usecases/supporting/FlyToDestination.md)|
| SC8           | Image Capture and Analysis  | [ImageCaptureAndAnalysis.md](usecases/supporting/ImageCaptureAndAnalysis.md)|
| SC9           | Item Drop |[ItemDrop.md](usecases/supporting/ItemDrop.md)|
| SC10          | Reserved Airspace |[ReservedAirspace.md](usecases/supporting/ReservedAirspace.md)|
| SC11          | Synchronized Takeoff  | [SynchronizedTakeoff.md](usecases/supporting/SynchronizedTakeoff.md)|
| SC12          | Victim Confirmation  | [VictimConfirmation.md](usecases/supporting/VictimConfirmation.md)|

<a name="GeneralExceptions"> </a>

### General Exception Cases apply across all other use cases 

| Use Case      | Description                  | Link  |
| ------------- |-------------                    | -----     |
|   EC1         | Loss of signal         | [LossOfSignal.md](usecases/general_exceptions/LossOfSignal.md) |
|  EC2   | Geofence vicinity breach ||
|  EC3   | Mechanical failure ||
|  EC4   | Low Battery ||


