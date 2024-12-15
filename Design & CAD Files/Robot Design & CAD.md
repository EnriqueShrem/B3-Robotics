# Robot Design & CAD
The robot design has been defined analytically, considering the real applications for which was developed. 

## Kinematics:  
Joints:
- Joint 0: Fixed.
- Joint 1: Revolute.
- Joint 2: Revolute.
- Joint 3: Revolute.
- Joint 4: Revolute.
- Joint 5: Prismatic

Links:
- Link 0 (base link): Does not add any limitation for the robot movement, but contributes to the vertical (z axis of base) range.
- Link 1: Contributes in range and allows movement normal and away from the base z axis direction.
- Link 2: Allows the movement towards the base and contributes to the movement normal and away from the base z axis direction.
- Link 3: The link rotates holding link 4 and limiting its motion, contributes to the range normal and away from the base z axis direction.
- Link 4: Allows and sets the maximun range at the base z axis direction, also rotates for manipulability, sets the range normal and away from the base z axis.
- EE (end effector): Attached to the end of link 4, can be defined and adapted for a particullar use.


## Isometric View of Assembly:

<p align="center">
  <img src="Design%20Gallery/isometric.jpeg" style="width:30%; height:30%;">
</p>

[See Design Gallery](Design%20Gallery)

## Assembly Drawing:
<p align="center">
  <img src="Design%20Gallery/drawing.jpeg" style="width:80%; height:80%;">
</p>

[See CAD Files](CAD%20Files)

## Robot Movement:
### Defined limits:
<p align="center">
  <img src="Design%20Gallery/topangles.png" style="width:50%; height:50%;">
</p>
<p align="center">
  <img src="Design%20Gallery/sideangles.png" style="width:50%; height:50%;">
</p>

### Achieved Movement:
<p align="center">
  <img src="Design%20Gallery/robotmov1.png" style="width:50%; height:50%;">
</p>
<p align="center">
  <img src="Design%20Gallery/robotmov.png" style="width:30%; height:30%;">
</p>
