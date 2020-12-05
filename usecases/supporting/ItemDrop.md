## Use Case:  Item drop

**ID**

SC9

**Description**

A UAV delivers an item such as a flotation device or defibrillator

**Invoked by**

| [River and Ice Rescue](../main/RiverRescue.md) | [Item Delivery](../main/ItemDelivery.md)| [AccidentSurveillance](../main/AccidentSurveillance.md) | [StructuralFire](../main/StructuralFire.md) | [EnvironmentalSampling](../main/EnvironmentalSampling.md) |
| :------: | :--------: | :--------: | :------: |:------: |
|   | x |   |   |  |


**Primary Actor**

- Semi-Autonomous UAV

**Supporting Actors**

- Mission Commander

**Stakeholders and Interests**

- Emergency responders
- General public

**Pre-Conditions**

- UAV is equipped with a carry-release mechanism based on either a parachute or a reel device
- The weight of the item to be delivered is within the safe operating payload of the UAV
- The item to be delivered has been attached to the UAV's carry mechanism

**Post Conditions**

_Success end condition:_

The UAV successfully delivers the item to the assigned location.

_Failure end condition:_

The UAV fails to deliver the device to the assigned location, drops it in an incorrect position or onto a person

**Trigger**

The UAV receives a command to deliver the item

## Main Success Scenario

1. The UAV takes-off and flies to the designated delivery coordinates
2. The UAV starts streaming video
3. The video is displayed in the UI for a human operator
4. The UAV uses onboard vision to determine a safe drop point appropriate for the task at hand
5. The UAV positions itself at the targeted drop point
6. The UAV requests permission from the human operator to drop the item
7. The human operator gives permission for the drop
8. The UAV lowers the item at the drop point
9. The human operator confirms that the drop is completed
10. The UAV moves to a safe observation point and awaits further instructions.

## Exceptions

1. All ubiquitous exceptions are handled.

2. The carry mechanism fails to activate when commanded
   * 2.1 The operator attempts a manual command
      * 2.1.2  If the carry mechanism continues to fail, the operator recalls the UAV

3. In step 4, the UAV is unable to find a safe drop point in the vicinity of the coordinates, and the human operator uses the video stream to manually identify the drop point. 
   
4. In step 7 the operator refuses permission for the drop point proposed by the drone and either:
   * 4.1 Suggests an alternate drop position
   * 4.2 or aborts the drop

[Return to use case list](../../README.md)
