
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

```
%Import the robot from URDF
robot = importrobot('ROBOT_/urdf/ROBOT_.urdf');

%Add gravity
robot.Gravity = [0 0 -9.80665];

%Add another massless coordinate frame for the end-effector
eeOffset = -0.450;
eeBody = robotics.RigidBody('EE');
eeBody.Mass = 0;
eeBody.Inertia = [0 0 0 0 0 0];
setFixedTransform(eeBody.Joint,trvec2tform([eeOffset 0 0]));
addBody(robot,eeBody,'link4');

%Display robot details
showdetails(robot);
show(robot)

%Number of samples
numSamples = 10000;

%Initialize workspace points
workspacePoints = zeros(numSamples, 3);

% Sample configurations and compute forward kinematics
for i = 1:numSamples
    % Generate random configuration
    config = randomConfiguration(robot);
    
    % Compute end-effector position
    tform = getTransform(robot, config, 'EE');  % Direct reference to 'end_effector'
    
    % Extract position (translation part of transform matrix)
    workspacePoints(i, :) = tform(1:3, 4)';
end

% Plot the workspace
hold on
scatter3(workspacePoints(:,1), workspacePoints(:,2), workspacePoints(:,3), '.');
title('Robot Workspace');
xlabel('X');
ylabel('Y');
zlabel('Z');
axis equal;
grid on;
```

## Simulation Results
### Simulation video:
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


