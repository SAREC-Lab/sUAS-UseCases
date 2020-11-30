# Use Cases for Emergency Response Missions with Small Unmanned Aerial Systems

If you would like to use these use-cases we ask you to reference our paper: <br><br>
**Jane Cleland-Huang, Ankit Agrawal, Md Nafee Al Islam, Eric Tsai, Maxime Van Speybroeck, Michael Vierhauser:
``Requirements-driven configuration of emergency response missions with small aerial vehicles''. Software Product Line Conference (SPLC) 2020: 26:1-26:12**
([bib available here](SPLC2020.txt))

Special thanks to the South Bend Fire Fighters for all of their input.

Please note: The import and inter-linking of these uses cases is in progress.

*Main Use Cases*

| Use Case      | Description                 | Contrib. Stakeholders              | Main Use Case  |
| ------------- |-------------                    | -----                              |            -----|    
| UC1           | River Search & Rescue           | South Bend Firefighters |[RiverRescue.md](usecases/main/RiverRescue.md ) 
| UC2           |Ice Rescue                       |   n/a |[IceRescue.md](usecases/main/IceRescue.md ) 
| UC3           |Item Delivery         |    DeLive, Cardiac Science | [ItemDelivery.md](usecases/main/ItemDelivery.md)
| UC4           |Traffic Accidents                |    South Bend Firefighters | [AccidentSurveillance.md](usecases/main/AccidentSurveillance.md)
| UC5           | Structural Fires                |    South Bend Firefighters | [StructuralFire.md](usecases/main/StructuralFire.md)
| UC6           | Water Sampling                  |    Environmental Scientists | [WaterSampling.md](usecases/main/WaterSampling.md)
| UC7           | Air Sampling                    |    Environmental Scientists | [AirSampling.md](usecases/main/AirSampling.md)

*Supporting Use Cases*

| Use Case      | Description                  | Link  |
| ------------- |-------------                    | -----     |
|   SC1         | Initiate Area Search           | [InitiateAreaSearch.md](usecases/supporting/InitiateAreaSearch.md) |
|   SC2         | Victim Confirmation  | [VictimConfirmation.md](usecases/supporting/VictimConfirmation.md)|
|   SC3         | Active Tracking  | [ActiveTracking.md](usecases/supporting/ActiveTracking.md)|
|   SC4         | Perform Search | [PerformSearch.md](usecases/supporting/PerformSearch.md)|
|   SC5        | Synchronized Takeoff  | [SynchronizedTakeoff.md](usecases/supporting/SynchronizedTakeoff.md)|
|   SC6         | Image Capture and Analysis  | [ImageCaptureAndAnalysis.md](usecases/supporting/ImageCaptureAndAnalysis.md)|
|   SC7        | End Mission  | [EndMission.md](usecases/supporting/EndMission.md)|
|   SC8        | Flight Authorization  | [FlightAuthorization.md](usecases/supporting/FlightAuthorization.md)|
|  SC9 | Item Drop |[ItemDrop.md](usecases/supporting/ItemDrop.md)|
|  SC10 | Reserved Airspace |[ReservedAirspace.md](usecases/supporting/ReservedAirspace.md)|
| SC11 | Fly to destination |[FlyToDestination.md](usecases/supporting/FlyToDestination.md)|
| SC12 | Activate and Arm | [ActivateAndArm.md](usecases/supporting/ActivateAndArm.md)|

*<a name="GeneralExceptions">General Exception Cases</a> apply across all other use cases*

| Use Case      | Description                  | Link  |
| ------------- |-------------                    | -----     |
|   EC1         | Loss of signal         | [LossOfSignal.md](usecases/general_exceptions/LossOfSignal.md) |
|  EC2   | Geofence vicinity breach ||
|  EC3   | Mechanical failure ||
|  EC4   | Low Battery ||


