
We are working on a project exploring safety-critical aspects, particularly hazards associated with the use of small unmanned aerial systems (sUAS)- especially hazards connected with human-drone interactions. 
As a precursor to this study, we have developed a set of hazard trees that explore specific human-interaction hazards and their possible mitigations. 
Given your expertise with sUAS we would like to ask you to contribute to this open source resource which is available [here](README.md).  
We plan to create a knowledge base that will be useful to sUAS system developers in the future.  All contributors will be fully acknowledged.



 For example, the following hazard tree examines the impact of communication failures upon the operator.  


[![](human-interaction-hazards/figures/communication.png)](#)
- System level hazards are shown in gray while human-related hazards are shown in yellow, green, and blue.
- <sub>[![](human-interaction-hazards/icons/s-icon.PNG)](#) </sub> Green hazards depict loss of situational awareness, and represent hazards in which the operator doesn’t fully understand what the UAVs are doing or their current health etc.  

- <sub>[![](human-interaction-hazards/icons/e-icon.PNG)](#) </sub> Yellow hazards represent loss of empowerment, in which the operator isn’t able to perform an action that they might like/need to do. 

- <sub>[![](human-interaction-hazards/icons/h-icon.PNG)](#) </sub> Finally, blue hazards represent mistakes (deliberate or accidental) that the operators might make.

For each of these human-related hazards we have provided a preliminary list of potential mitigations.  
For example the hazard CX2: “The operator is unable to receive status data from the sUAS’ and loses situational awareness” includes the mitigation that 
“The The approximate position and the uncertainty of the sUAS current position on the map must be visually depicted
(e.g., by creating an increasingly large 'circle' around the last known, or projected position of the sUAS.”

We would invite you to provide feedback in two different ways.  
First -- please take a look at the hazard trees here (URL) and then use the feedback form or the discussion forum to offer comments and suggestions. 
Second -- we are eliciting human-drone interaction stories that include accounts of when “things went wrong”.  
For example in one of our stories, we were running maintenance in the lab and wanted the motors to spin.  
So we disabled GPS related arming checks, but forgot about this and later when flying outside the sUAS took off without GPS arming checks. 
In this case we realized something was wrong and immediately landed the sUAS -- unfortunately in a very hard landing.  
This was an example of human error which could have been addressed by following the mitigations prescribed in the preflight checks. 
If you have these kinds of ‘human-error’ stories, please share them through this link (GOOGLE FORM LINK). 
We plan to publish them to the Github repository as a shared resource - and you will have the choice for your name to appear or for them to be posted anonymously.

Please email Jane Cleland-Huang (JaneHuang@nd.edu) or Michael Vierhauser (michael.vierhauser@jku.at) 
