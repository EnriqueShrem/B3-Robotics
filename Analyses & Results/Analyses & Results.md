## Payload Estimation 
Each link must be able to withstand the stresses that are imposed by the payload.  

Apply the bending stress equation to each link:  

$$\sigma = \frac{M \cdot c}{I}$$

σ: Bending stress in the link (Pa).  
𝑀: Bending moment due to payload and link mass.  
𝑐: Distance from the neutral axis to the outermost fiber (depends on link cross-section).  
𝐼: Second moment of area of the link cross-section.  

The bending stress 𝜎 must not exceed the yield strength of the link material:  
𝜎 ≤ 𝜎yield

## Robot's Reach / Range of Motion
The range of motion of the end effector, also known as robot's reach, can be found analytically but also demonstrated using software such as MATLAB:
<p align="center">
  <img src="range.png" alt="Inverse Kinematics (Simulink)"style="width:60%; max-width:600px, height:60%;">
</p>
<p align="center">
  <img src="rangetop.png" alt="Inverse Kinematics (Simulink)"style="width:50%; max-width:600px, height:50%;">
</p>
<p align="center">
  <img src="rangefront.png" alt="Inverse Kinematics (Simulink)"style="width:50%; max-width:600px, height:50%;">
</p>
For this demonstration a sample of 10000 random robot configurations has been used to plot the end effector position at each of these configurations.


## Simulation Results

<p align="center">
<a  href="https://youtu.be/6YlWMIfZ7P8" target="_blank">
    <img src="https://img.youtube.com/vi/6YlWMIfZ7P8/0.jpg" alt="Simulation Video" style="width:50%; max-width:600px, height:50%;">
</a>
</p>

## Kinematic Graphs
### Position Trajectory and Forward Kinematics

<p align="center">
  <img src="Position.jpeg" alt="Position Trajectory and Forward Kinematics" style="width:50%; max-width:600px, height:50%;">
</p>

### Velocity Trajectory and Jacobian
<p align="center">
  <img src="Velocity.jpeg" alt="Velocity Trajectory and Jacobian" style="width:50%; max-width:600px, height:50%;">
</p>


