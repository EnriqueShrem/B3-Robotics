
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

## Payload Analysis
MATLAB:

```
% Payload Calculation for SCARA Robot - Corrected Torque Contributions
% Robot Link Properties (mass in kg)
m0 = 2.36614;     % Link 0 mass
m1 = 3.68669;     % Link 1 mass
m2 = 4.65743;     % Link 2 mass
m3 = 1.83344;     % Link 3 mass
m5 = 0.28631;     % End-effector mass

% Center of Mass for each link (meters, relative to base or prior joints)
com1 = 0.07961;   % COM distance of Link 1 along x-axis
com2 = 0.10027;   % COM distance of Link 2 from Joint 2
com3 = 0.15288;   % COM distance of Link 3

% Link Lengths (meters)
L1 = 0.3;        % Length of Link 1
L2 = 0.304;      % Length of Link 2
H2 = 0.285;      % End-effector height

% Gravitational Acceleration
g = 9.81;

% Actuator Torque Limits (Realistic values, Nm)
max_torque = [50; 25];  % Adjust these values based on motor specs

% Initialize Payload
payload_mass = 0; 
increment = 0.1;  % Payload increment (kg)

% Torque Calculation Loop
while true
    % Torque at Joint 1 (cumulative weight of all links + payload)
    torque_joint1 = (m1 * g * (L1/2)) + (m2 * g * (L1 + L2/2)) ...
                  + (m3 * g * (L1 + L2 + com3)) + (payload_mass * g * (L1 + L2));
    
    % Torque at Joint 2 (link 2, link 3, and payload)
    torque_joint2 = (m2 * g * (L2/2)) + (m3 * g * (L2 + com3)) + (payload_mass * g * L2);

    % Check if torques exceed actuator limits
    if torque_joint1 > max_torque(1) || torque_joint2 > max_torque(2)
        break;
    end

    % Increment payload
    payload_mass = payload_mass + increment;
end

% Display Results
fprintf('Maximum payload capacity: %.2f kg\n', payload_mass - increment);

```
Maximum payload Capacity : 1.70kg
