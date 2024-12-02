# Mathematical Models
## Forward Kinematics (MATLAB)
```
% Forward Kinematics
% General DH Transformation Matrix
function T = DHTransformationMat(a, alpha, d, theta)
    T = [cos(theta) -sin(theta)*cos(alpha) sin(theta)*sin(alpha) a*cos(theta);
        sin(theta) cos(theta)*cos(alpha) -cos(theta)*sin(alpha) a*sin(theta);
        0 sin(alpha) cos(alpha) d;
        0 0 0 1];
end

syms theta1 theta2 theta3 ;
syms L1 L2 L3 L4 L5 L6;

% Robot DH Table
DH_table = [0,      0,      L1,     0;
            L3,     0,      L2,     theta1;
            0,      pi/2,   L4,     theta2;
            0,      pi/2,   L5,     theta3;
            0,      0,      L6,     0];

T01 = DHTransformationMat(DH_table(1, 1), DH_table(1, 2), DH_table(1, 3), DH_table(1, 4));
T12 = DHTransformationMat(DH_table(2, 1), DH_table(2, 2), DH_table(2, 3), DH_table(2, 4));
T23 = DHTransformationMat(DH_table(3, 1), DH_table(3, 2), DH_table(3, 3), DH_table(3, 4));
T34 = DHTransformationMat(DH_table(4, 1), DH_table(4, 2), DH_table(4, 3), DH_table(4, 4));
T45 = DHTransformationMat(DH_table(5, 1), DH_table(5, 2), DH_table(5, 3), DH_table(5, 4));

% Cumulative transformation matrices
T1 = T01;                  % Joint 1
T2 = T1 * T12;             % Joint 2
T3 = T2 * T23;             % Joint 3
T4 = T3 * T34;             % Joint 4
T5 = T4 * T45              % Joint 5 (End Effector)

T5 = simplify(T5)
```

## Inverse Kinematics (Simulink)

<p align="center">
  <img src="Mathematical%20Models/Inverse%20Simulink.jpeg" alt="Inverse Kinematics (Simulink)" height = %30 h="600">
</p>
