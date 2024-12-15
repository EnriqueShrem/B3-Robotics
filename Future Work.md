# Future Work

## End Effector Development
Conventional end-effectors such as grippers and vacuum nozzles will not be suitable for the robot movements nor capable of realizing the proposed tasks such as liquid pouring, flask handeling, pick and place, etc. Therefore a development of custom end-effector will be necessary.

## Payload Estimation 
Each link must be able to withstand the stresses that are imposed by the payload.  

This can be adressed by applying the bending stress equation to each link:  

$$\sigma = \frac{M \cdot c}{I}$$

σ: Bending stress in the link (Pa).  
𝑀: Bending moment due to payload and link mass.  
𝑐: Distance from the neutral axis to the outermost fiber (depends on link cross-section).  
𝐼: Second moment of area of the link cross-section.  

The bending stress 𝜎 must not exceed the yield strength of the link material:  
𝜎 ≤ 𝜎yield

 Also this can be estimated by using a simulation software that employs FEA method for analysis to end up with better results.

