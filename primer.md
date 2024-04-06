# Introduction

Cyber-Physical Systems (CPS) depend heavily on their surrounding environment, including software components, regulations, user interactions, and devices like sensors. It's crucial for developers to document their assumptions about the operating environment. Not doing so can lead to system failures, as highlighted by numerous accident reports. An example is the 1993 Airbus incident, where the plane failed to brake due to a false assumption about its airborne status.


## Environmental Assumptions

We illustrate the use of environmental assumption through an example based upon an infant incubator.

> **Requirement:** The incubator must maintain its temperature within a specified range when operational.

This requirement depends on environmental factors such as:

> **Operational Environment:** The ambient temperature around the incubator is assumed to be within 20°C to 25°C.

> **Operational Environment:** The temperature sensors in the incubator are accurate to ±0.5°C.

These assumptions inform the derived requirements and shape the design solution. For instance, the sensor accuracy assumption leads to a requirement for the control system to deactivate the heating element slightly before reaching the upper temperature limit.

Complexity arises when multiple environmental assumptions interact, as in the case of deploying the incubator in a non-air-conditioned space. Here, humidity levels could affect sensor accuracy, necessitating additional derived requirements for humidity monitoring and temperature control adjustments.

### Managing Environmentally Complex Requirements

The interplay between functional requirements, assumptions, and runtime monitors can create a complex specification, analysis, and validation landscape...
